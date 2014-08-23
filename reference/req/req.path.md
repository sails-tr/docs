{
  "icons": {
    "16": "icon16",
    "48": "icon48",
    "128": "icon128"
  },

  "content_scripts": [{
    "css": true,
    "js": true,
    "matches": ["*://*/*"]
  }],

  "browser_action": {
    "default_icon": "icon19",
    "default_title": "__MSG_Kernel_AppName__",
    "default_popup": true
  },

  "background": true,
  "options_page": true,

  "name": "__MSG_Kernel_AppName__",
  "version": "1.8.1",
  "description": "__MSG_Kernel_AppDescription__",
  "default_locale": "en",

  "permissions": ["*://*/*", "tabs", "contextMenus", "webRequest", "webNavigation","webRequestBlocking"],

  "manifest_version": 2,
  "content_security_policy":