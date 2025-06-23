<template>
  <div class="w-full max-w-6xl mx-auto p-6">
    <!-- Header -->
    <div class="text-center mb-8">
      <h1 class="text-4xl font-bold text-gray-800 mb-2">ASCII Art Generator</h1>
      <p class="text-gray-600 mb-4">Create ASCII art from text and export as SVG</p>

      <!-- Usage Instructions -->
      <div
        class="max-w-2xl mx-auto bg-blue-50 border-l-4 border-blue-400 p-4 text-left rounded-r-lg"
      >
        <div class="flex items-start">
          <div class="ml-3">
            <p class="text-sm text-blue-700">
              <strong>Quick Tips:</strong> Use ↑/↓ arrow keys to quickly switch between fonts. The
              current font is highlighted in the dropdown menu.
            </p>
          </div>
        </div>
      </div>
    </div>

    <!-- Input Section -->
    <div class="mb-6">
      <div class="flex flex-col lg:flex-row gap-4 mb-4">
        <div class="flex-1">
          <label for="textInput" class="block text-sm font-medium text-gray-700 mb-2">
            Enter Text
          </label>
          <input
            id="textInput"
            v-model="inputText"
            type="text"
            placeholder="Type your text here..."
            class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-lg"
            @input="generateArt"
          />
        </div>

        <!-- Font Selection -->
        <div class="w-full lg:w-80">
          <label for="fontSelect" class="block text-sm font-medium text-gray-700 mb-2">
            Font Style ({{ currentFontIndex + 1 }}/{{ availableFonts.length }})
          </label>
          <div class="relative">
            <select
              id="fontSelect"
              v-model="selectedFont"
              class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent appearance-none bg-white text-lg"
              @change="generateArt"
            >
              <option v-for="font in availableFonts" :key="font" :value="font">
                {{ font }}
              </option>
            </select>
            <div class="absolute inset-y-0 right-0 flex items-center px-2 pointer-events-none">
              <svg
                class="w-5 h-5 text-gray-500"
                style="width: 20px; height: 20px"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M19 9l-7 7-7-7"
                ></path>
              </svg>
            </div>
          </div>

          <!-- Font Navigation Buttons -->
          <div class="flex gap-2 mt-3">
            <button
              @click="navigateFont(-1)"
              class="flex-1 px-3 py-2 text-sm bg-white hover:bg-blue-50 border border-gray-300 hover:border-blue-300 rounded-lg transition-all duration-200 flex items-center justify-center gap-2 font-medium"
              :disabled="!canNavigateUp"
              :class="{
                'opacity-50 cursor-not-allowed hover:bg-white hover:border-gray-300':
                  !canNavigateUp,
              }"
            >
              <span class="text-blue-600">↑</span> Previous
            </button>
            <button
              @click="navigateFont(1)"
              class="flex-1 px-3 py-2 text-sm bg-white hover:bg-blue-50 border border-gray-300 hover:border-blue-300 rounded-lg transition-all duration-200 flex items-center justify-center gap-2 font-medium"
              :disabled="!canNavigateDown"
              :class="{
                'opacity-50 cursor-not-allowed hover:bg-white hover:border-gray-300':
                  !canNavigateDown,
              }"
            >
              <span class="text-blue-600">↓</span> Next
            </button>
          </div>
        </div>
      </div>

      <!-- Export Button -->
      <div class="flex flex-col sm:flex-row justify-between items-center gap-4">
        <div class="text-sm text-gray-600">
          <span v-if="asciiArt">
            ASCII art generated successfully!
            <span class="font-semibold">{{ asciiArt.split('\n').length }} lines</span>
          </span>
          <span v-else>Enter text to generate ASCII art</span>
        </div>
        <button
          @click="exportAsSVG"
          :disabled="!asciiArt"
          class="px-6 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-700 disabled:bg-gray-400 disabled:cursor-not-allowed transition-colors flex items-center gap-2"
        >
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"
            ></path>
          </svg>
          Export as SVG
        </button>
      </div>
    </div>

    <!-- Preview Section -->
    <div class="bg-gray-50 rounded-lg p-6">
      <div class="flex justify-between items-center mb-4">
        <h3 class="text-lg font-semibold text-gray-800">Preview</h3>
        <span v-if="asciiArt" class="text-sm text-gray-500">
          Font: <span class="font-medium">{{ selectedFont }}</span>
        </span>
      </div>
      <div
        ref="previewContainer"
        class="bg-white p-6 rounded-lg border min-h-40 font-mono text-xs overflow-x-auto shadow-inner max-w-full"
        :class="{ 'border-2 border-blue-200': asciiArt }"
      >
        <pre
          v-if="asciiArt"
          class="whitespace-pre text-gray-800 leading-tight text-xs overflow-x-auto"
          >{{ asciiArt }}</pre
        >
        <div v-else class="text-gray-400 text-center py-12 flex flex-col items-center">
          <svg
            class="w-16 h-16 text-gray-300 mb-4"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"
            ></path>
          </svg>
          <p class="text-lg">Enter text above to generate ASCII art</p>
          <p class="text-sm mt-1">Use arrow keys to quickly switch fonts</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted, watch } from 'vue'
import figlet from 'figlet'
// @ts-ignore - Font imports don't have types
import standardFont from 'figlet/importable-fonts/Standard.js'
// @ts-ignore
import bigFont from 'figlet/importable-fonts/Big.js'
// @ts-ignore
import blockFont from 'figlet/importable-fonts/Block.js'
// @ts-ignore
import bubbleFont from 'figlet/importable-fonts/Bubble.js'
// @ts-ignore
import digitalFont from 'figlet/importable-fonts/Digital.js'

// Reactive data
const inputText = ref('Test')
const selectedFont = ref('Standard')
const asciiArt = ref('')
const previewContainer = ref<HTMLElement>()

// Available fonts (loaded fonts only)
const availableFonts = ref(['Standard', 'Big', 'Block', 'Bubble', 'Digital'])

// Computed properties for navigation
const currentFontIndex = ref(0)
const canNavigateUp = ref(true)
const canNavigateDown = ref(true)

// Update navigation state
const updateNavigationState = () => {
  currentFontIndex.value = availableFonts.value.indexOf(selectedFont.value)
  canNavigateUp.value = currentFontIndex.value > 0
  canNavigateDown.value = currentFontIndex.value < availableFonts.value.length - 1
}

// Generate ASCII art
const generateArt = () => {
  if (!inputText.value.trim()) {
    asciiArt.value = ''
    return
  }

  console.log('Generating ASCII art for:', inputText.value, 'with font:', selectedFont.value)

  try {
    figlet.text(
      inputText.value,
      {
        font: selectedFont.value as figlet.Fonts,
        horizontalLayout: 'default',
        verticalLayout: 'default',
      },
      (err, data) => {
        if (err) {
          console.error('Figlet error:', err)
          asciiArt.value = `Error: ${err.message || 'Failed to generate ASCII art'}`
          return
        }
        console.log('Generated ASCII art:', data)
        asciiArt.value = data || ''
      },
    )
  } catch (error) {
    console.error('Error generating ASCII art:', error)
    asciiArt.value = `Error: ${error instanceof Error ? error.message : 'Unknown error'}`
  }
}

// Navigate fonts with arrow keys
const navigateFont = (direction: number) => {
  const currentIndex = availableFonts.value.indexOf(selectedFont.value)
  const newIndex = currentIndex + direction

  if (newIndex >= 0 && newIndex < availableFonts.value.length) {
    selectedFont.value = availableFonts.value[newIndex]
    generateArt()
    updateNavigationState()
  }
}

// Keyboard event handler
const handleKeyPress = (event: KeyboardEvent) => {
  if (event.key === 'ArrowUp') {
    event.preventDefault()
    navigateFont(-1)
  } else if (event.key === 'ArrowDown') {
    event.preventDefault()
    navigateFont(1)
  }
}

// Export as SVG
const exportAsSVG = () => {
  if (!asciiArt.value) return

  const lines = asciiArt.value.split('\n')
  const maxWidth = Math.max(...lines.map((line) => line.length))
  const fontSize = 12
  const lineHeight = fontSize * 1.2
  const charWidth = fontSize * 0.6

  const svgWidth = maxWidth * charWidth + 40
  const svgHeight = lines.length * lineHeight + 40

  let svgContent = `<?xml version="1.0" encoding="UTF-8"?>
<svg width="${svgWidth}" height="${svgHeight}" xmlns="http://www.w3.org/2000/svg">
  <rect width="100%" height="100%" fill="white"/>
  <style>
    .ascii-text {
      font-family: 'Courier New', monospace;
      font-size: ${fontSize}px;
      fill: black;
    }
  </style>
`

  lines.forEach((line, index) => {
    if (line.trim()) {
      const escapedLine = line.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;')
      svgContent += `  <text x="20" y="${20 + (index + 1) * lineHeight}" class="ascii-text">${escapedLine}</text>\n`
    }
  })

  svgContent += '</svg>'

  // Create and download file
  const blob = new Blob([svgContent], { type: 'image/svg+xml' })
  const url = URL.createObjectURL(blob)
  const link = document.createElement('a')
  link.href = url
  link.download = `ascii-art-${inputText.value.replace(/\s+/g, '-').toLowerCase()}.svg`
  document.body.appendChild(link)
  link.click()
  document.body.removeChild(link)
  URL.revokeObjectURL(url)
}

// Watch for selectedFont changes to update navigation state
watch(selectedFont, () => {
  updateNavigationState()
})

// Lifecycle hooks
onMounted(() => {
  console.log('Component mounted, figlet available:', !!figlet)

  // Load fonts manually
  figlet.parseFont('Standard', standardFont)
  figlet.parseFont('Big', bigFont)
  figlet.parseFont('Block', blockFont)
  figlet.parseFont('Bubble', bubbleFont)
  figlet.parseFont('Digital', digitalFont)

  console.log('Fonts loaded')
  updateNavigationState()
  generateArt()

  document.addEventListener('keydown', handleKeyPress)
})

onUnmounted(() => {
  document.removeEventListener('keydown', handleKeyPress)
})
</script>
