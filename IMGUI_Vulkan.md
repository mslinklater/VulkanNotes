# DearIMGUI Vulkan Implementation

## Data Structures

### ImGui_ImplVulkan_InitInfo

Passed in to ImGui from the application to give ImGui all the Vulkan info it needs to hook in to the rendering

|Type|Description|
|---|---|
|VkInstance||
|VkPhysicalDevice||
|VkDevice||
|uint32_t||
|VkQueue||
|VkPipelineCache||
|VkDescriptorPool||
|uint32_t||
|uint32_t||
|uint32_t||
|VkSampleCountFlagBits||
|const VkAllocatorCallbacks*||
|void (*CheckVkResults)(VkResult)||

## Methods

### Init

### Shutdown

### NewFrame

### RenderDrawData

### CreateFontsTexture

### DestroyFontUploadObjects

### SetMinImageCount

### AddTexture

### RemoveTexture

### LoadFunctions

### CreateOrResizeWindow

### DestroyWindow

### SelectSurfaceFormat

### SelectPresentMode

### GetMinImageCountFromPresentMode
