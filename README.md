# Magento 2 Module for mmenu-light.js (3.1.1)

**This repo is just an integration of original js-library including css into Magento 2.**

> The (extremely) lightweight alternative to the mmenu.js plugin for creating off-canvas mobile menus with the exact look and feel.

See original repository for more information: https://github.com/FrDH/mmenu-light

### Installation

```bash
cd <magento_root>
composer require mediarox/module-js-mmenu-light
bin/magento setup:upgrade
```
### Imagined example for topMenu

```php
?>
<script>
    let navigationSelector = 'nav.navigation';
    let navigationToggleSelector = '[data-action="toggle-nav"]';
    let navigationActiveUlSelector = 'li.active > ul.submenu';
    let navigationMobileMediaQuery = '(max-width: 768px)';

    require([
        'jquery',
        'mmenuLight'
    ], function ($) {
    
        // validate required elements
        const navigation = document.querySelector(navigationSelector);
        const navigationToggle = document.querySelector(navigationToggleSelector);
        if(!navigation || !navigationToggle) return;
        
        // init mmmenu
        const mobileMenu = new MmenuLight(navigation, navigationMobileMediaQuery);
        const mobileMenuNavigator = mobileMenu.navigation();
        const mobileMenuDrawer = mobileMenu.offcanvas();
        
        // set active panel if needed
        const activePanel = document.querySelector(navigationActiveUlSelector);
        if(activePanel) {
            mobileMenuNavigator.openPanel(activePanel);
        }
        
        // add click/open event
        navigationToggle.addEventListener("click", (event) => {
            event.preventDefault();
            mobileMenuDrawer.open();
        });
    });
</script>
```