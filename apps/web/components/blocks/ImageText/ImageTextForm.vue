<template>
  <div class="sticky top-[52px] h-[calc(100vh-52px)] overflow-y-auto">
    <form class="w-full absolute bg-white" data-testid="image-text-form">
      <UiAccordionItem
        v-model="imageGroupOpen"
        summary-active-class="bg-neutral-100 border-t-0"
        summary-class="w-full hover:bg-neutral-100 px-4 py-5 flex justify-between items-center select-none border-b"
        data-testid="image-group"
      >
        <template #summary>
          <h2>Images</h2>
        </template>

        <div class="py-2">
          <div class="flex justify-between mb-2">
            <UiFormLabel>Image XL (Desktop) </UiFormLabel>
          </div>
          <label>
            <SfInput v-model="uiImageTextBlock.image.wideScreen" type="text" data-testid="wide-screen-input">
              <template #suffix>
                <label for="image-tablet" class="rounded-lg cursor-pointer">
                  <input
                    id="image-tablet"
                    v-model="uiImageTextBlock.image.wideScreen"
                    type="text"
                    class="invisible w-8"
                  />
                </label>
              </template>
            </SfInput>
            <span class="typography-text-xs text-neutral-700">Recommended dimensions: 1920 x 1080 px </span>
          </label>
        </div>

        <div class="py-2">
          <div class="flex justify-between mb-2">
            <UiFormLabel>Image L (Desktop) </UiFormLabel>
          </div>
          <label>
            <SfInput v-model="uiImageTextBlock.image.desktop" type="text" data-testid="large-screen-input">
              <template #suffix>
                <label for="image-tablet" class="rounded-lg cursor-pointer">
                  <input id="image-tablet" v-model="uiImageTextBlock.image.desktop" type="text" class="invisible w-8" />
                </label>
              </template>
            </SfInput>
            <span class="typography-text-xs text-neutral-700">Recommended dimensions: 1024 x 576 px</span>
          </label>
        </div>

        <div class="py-2">
          <div class="flex justify-between mb-2">
            <UiFormLabel>Image M (Laptop) </UiFormLabel>
          </div>
          <label>
            <SfInput v-model="uiImageTextBlock.image.tablet" type="text" data-testid="medium-screen-input">
              <template #suffix>
                <label for="image-tablet" class="rounded-lg cursor-pointer">
                  <input id="image-tablet" v-model="uiImageTextBlock.image.tablet" type="text" class="invisible w-8" />
                </label>
              </template>
            </SfInput>
            <span class="typography-text-xs text-neutral-700">Recommended dimensions: 768 x 432 px</span>
          </label>
        </div>

        <div class="py-2">
          <div class="flex justify-between mb-2">
            <UiFormLabel>Image S (Mobile) </UiFormLabel>
          </div>
          <label>
            <SfInput v-model="uiImageTextBlock.image.mobile" type="text" data-testid="small-screen-input">
              <template #suffix>
                <label for="image-mobile" class="rounded-lg cursor-pointer">
                  <input
                    id="image-mobile"
                    v-model="uiImageTextBlock.image.mobile"
                    data-testid="small-screen-input"
                    type="text"
                    class="invisible w-8"
                  />
                </label>
              </template>
            </SfInput>
            <span class="typography-text-xs text-neutral-700">Recommended dimensions: 320 x 320 px </span>
          </label>
        </div>

        <div class="py-2">
          <div class="flex justify-between mb-2">
            <UiFormLabel>Alt</UiFormLabel>
          </div>
          <label>
            <SfInput v-model="uiImageTextBlock.image.alt" type="text" data-testid="alt-input">
              <template #suffix>
                <label for="alt" class="rounded-lg cursor-pointer">
                  <input id="alt" v-model="uiImageTextBlock.image.alt" type="text" class="invisible w-8" />
                </label>
              </template>
            </SfInput>
          </label>
        </div>
        <fieldset class="py-2">
          <UiFormLabel>Image Alignment</UiFormLabel>

          <div class="mt-2 w-full inline-flex rounded-lg border border-gray-300 bg-white text-gray-700 overflow-hidden">
            <div
              for="align-left"
              class="flex items-center justify-center w-1/2 px-4 py-2 cursor-pointer text-sm"
              :class="{ 'bg-gray-100 text-gray-900 font-semibold': uiImageTextBlock.image.imageAlignment === 'left' }"
              data-testid="image-align-left"
              @click="uiImageTextBlock.image.imageAlignment = 'left'"
            >
              <SfIconCheck
                :class="{ invisible: uiImageTextBlock.image.imageAlignment !== 'left' }"
                class="mr-1 w-[1.1rem]"
              />

              Left
            </div>

            <div
              for="align-right"
              class="flex items-center justify-center w-1/2 px-4 py-2 cursor-pointer text-sm"
              :class="{ 'bg-gray-100 text-gray-900 font-semibold': uiImageTextBlock.image.imageAlignment === 'right' }"
              data-testid="image-align-right"
              @click="uiImageTextBlock.image.imageAlignment = 'right'"
            >
              <SfIconCheck
                :class="{ invisible: uiImageTextBlock.image.imageAlignment !== 'right' }"
                class="mr-1 w-[1.1rem]"
              />
              Right
            </div>
          </div>
        </fieldset>
      </UiAccordionItem>

      <UiAccordionItem
        v-model="textGroup"
        summary-active-class="bg-neutral-100 border-t-0"
        summary-class="w-full hover:bg-neutral-100 px-4 py-5 flex justify-between items-center select-none border-b"
        data-testid="text-group"
      >
        <template #summary>
          <h2>Text</h2>
        </template>

        <div class="py-2">
          <div class="flex justify-between mb-2">
            <UiFormLabel>Pre-title</UiFormLabel>
          </div>
          <label>
            <SfInput v-model="uiImageTextBlock.text.pretitle" type="text">
              <template #suffix>
                <label for="pretitle" class="rounded-lg cursor-pointer">
                  <input
                    id="pretitle"
                    v-model="uiImageTextBlock.text.pretitle"
                    data-testid="input-pre-title"
                    type="text"
                    class="invisible w-8"
                  />
                </label>
              </template>
            </SfInput>
          </label>
        </div>

        <div class="py-2">
          <div class="flex justify-between mb-2">
            <UiFormLabel>Main title</UiFormLabel>
          </div>
          <label>
            <SfInput v-model="uiImageTextBlock.text.title" type="text">
              <template #suffix>
                <label for="title" class="rounded-lg cursor-pointer">
                  <input
                    id="title"
                    v-model="uiImageTextBlock.text.title"
                    data-testid="input-title"
                    type="text"
                    class="invisible w-8"
                  />
                </label>
              </template>
            </SfInput>
          </label>
        </div>

        <div class="py-2">
          <div class="flex justify-between mb-2">
            <UiFormLabel>Sub title</UiFormLabel>
          </div>
          <label>
            <SfInput v-model="uiImageTextBlock.text.subtitle" type="text">
              <template #suffix>
                <label for="subtitle" class="rounded-lg cursor-pointer">
                  <input
                    id="subtitle"
                    v-model="uiImageTextBlock.text.subtitle"
                    data-testid="input-sub-title"
                    type="text"
                    class="invisible w-8"
                  />
                </label>
              </template>
            </SfInput>
          </label>
        </div>

        <div class="py-2">
          <UiFormLabel>HTML Description</UiFormLabel>
          <SfTextarea
            id="html-description"
            v-model="uiImageTextBlock.text.htmlDescription"
            data-testid="textarea-html"
            name="html-description"
            rows="3"
            class="min-h-[232px] mt-1 block w-full border border-gray-300 rounded-md shadow-sm sm:text-sm"
          />
        </div>

        <div class="py-2">
          <div class="flex justify-between mb-2">
            <UiFormLabel>Text Color</UiFormLabel>
          </div>
          <label>
            <SfInput v-model="uiImageTextBlock.text.color" type="text" data-testid="color-picker">
              <template #suffix>
                <label
                  for="primary-color"
                  :style="{ backgroundColor: uiImageTextBlock.text.color }"
                  class="border border-[#a0a0a0] rounded-lg cursor-pointer"
                >
                  <input id="primary-color" v-model="uiImageTextBlock.text.color" type="color" class="invisible w-8" />
                </label>
              </template>
            </SfInput>
          </label>
        </div>

        <fieldset class="py-2">
          <legend class="text-sm font-medium text-gray-700">Text Alignment</legend>

          <div class="mt-2 w-full inline-flex rounded-lg border border-gray-300 bg-white text-gray-700 overflow-hidden">
            <div
              for="text-align-left"
              data-testid="text-align-left"
              class="flex items-center justify-center w-1/3 px-4 py-2 cursor-pointer text-sm border-r"
              :class="{ 'bg-gray-100 text-gray-900 font-semibold': uiImageTextBlock.text.textAlignment === 'left' }"
              @click="uiImageTextBlock.text.textAlignment = 'left'"
            >
              <SfIconCheck
                :class="{ invisible: uiImageTextBlock.text.textAlignment !== 'left' }"
                class="mr-1 w-[1.1rem]"
              />
              Left
            </div>

            <div
              for="text-align-center"
              data-testid="text-align-center"
              class="flex items-center justify-center w-1/3 px-4 py-2 cursor-pointer text-sm border-r"
              :class="{ 'bg-gray-100 text-gray-900 font-semibold': uiImageTextBlock.text.textAlignment === 'center' }"
              @click="uiImageTextBlock.text.textAlignment = 'center'"
            >
              <SfIconCheck
                :class="{ invisible: uiImageTextBlock.text.textAlignment !== 'center' }"
                class="mr-1 w-[1.1rem]"
              />
              Center
            </div>

            <div
              for="text-align-right"
              data-testid="text-align-right"
              class="flex items-center justify-center w-1/3 px-4 py-2 cursor-pointer text-sm"
              :class="{ 'bg-gray-100 text-gray-900 font-semibold': uiImageTextBlock.text.textAlignment === 'right' }"
              @click="uiImageTextBlock.text.textAlignment = 'right'"
            >
              <SfIconCheck
                :class="{ invisible: uiImageTextBlock.text.textAlignment !== 'right' }"
                class="mr-1 w-[1.1rem]"
              />
              Right
            </div>
          </div>
        </fieldset>
      </UiAccordionItem>
      <UiAccordionItem
        v-model="buttonGroup"
        summary-active-class="bg-neutral-100 border-t-0"
        summary-class="w-full hover:bg-neutral-100 px-4 py-5 flex justify-between items-center select-none border-b"
        data-testid="button-group"
      >
        <template #summary>
          <h2>Button</h2>
        </template>

        <div class="py-2">
          <div class="flex justify-between mb-2">
            <UiFormLabel>Label</UiFormLabel>
          </div>
          <label>
            <SfInput v-model="uiImageTextBlock.button.label" type="text" data-testid="input-label">
              <template #suffix>
                <label for="button-label" class="rounded-lg cursor-pointer">
                  <input id="button-label" v-model="uiImageTextBlock.button.label" type="text" class="invisible w-8" />
                </label>
              </template>
            </SfInput>
          </label>
        </div>

        <div class="py-2">
          <div class="flex justify-between mb-2">
            <UiFormLabel>Link target</UiFormLabel>
          </div>
          <label>
            <SfInput v-model="uiImageTextBlock.button.link" type="text" data-testid="input-link">
              <template #suffix>
                <label for="button-label" class="rounded-lg cursor-pointer">
                  <input id="button-label" v-model="uiImageTextBlock.button.link" type="text" class="invisible w-8" />
                </label>
              </template>
            </SfInput>
          </label>
        </div>
        <fieldset class="py-2">
          <UiFormLabel>Outline</UiFormLabel>

          <div class="mt-2 w-full inline-flex rounded-lg border border-gray-300 bg-white text-gray-700 overflow-hidden">
            <div
              for="align-left"
              class="flex items-center justify-center w-1/2 px-4 py-2 cursor-pointer text-sm"
              data-testid="outline-primary"
              :class="{ 'bg-gray-100 text-gray-900 font-semibold': uiImageTextBlock.button.variant === 'primary' }"
              @click="uiImageTextBlock.button.variant = 'primary'"
            >
              <SfIconCheck
                :class="{ invisible: uiImageTextBlock.button.variant !== 'primary' }"
                class="mr-1 w-[1.1rem]"
              />

              Primary
            </div>

            <div
              for="align-right"
              class="flex items-center justify-center w-1/2 px-4 py-2 cursor-pointer text-sm"
              data-testid="outline-secondary"
              :class="{ 'bg-gray-100 text-gray-900 font-semibold': uiImageTextBlock.button.variant === 'secondary' }"
              @click="uiImageTextBlock.button.variant = 'secondary'"
            >
              <SfIconCheck
                :class="{ invisible: uiImageTextBlock.button.variant !== 'secondary' }"
                class="mr-1 w-[1.1rem]"
              />
              Secondary
            </div>
          </div>
        </fieldset>
      </UiAccordionItem>
    </form>
  </div>
</template>

<script setup lang="ts">
import type { ImageTextProps } from './types';
import { SfInput, SfTextarea, SfIconCheck } from '@storefront-ui/vue';
const { data } = useHomepage();
const { blockIndex } = useSiteConfiguration();
const uiImageTextBlock = computed(() => (data.value.blocks[blockIndex.value].options || {}) as ImageTextProps);

const imageGroupOpen = ref(false);
const buttonGroup = ref(false);
const textGroup = ref(false);
</script>
