# Glossary

**VkCommandBuffer** - Buffer object which holds command objects.

**VkCommandPool** - The command pool is where command buffers are allocated from. Normally each swapchain image has it's own command pool as part of the per-frame setup data.

**VkInstance** - The actual vulkan instance on the device. There is only one of these and it manages all Vulkan interactions for the entire system.
