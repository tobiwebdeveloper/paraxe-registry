# Theming and customisation

Load structural tokens first, then a theme and preset, then component CSS. Override CSS custom properties in your application scope rather than editing package component selectors. This preserves component contracts while allowing a local visual system.

Do not assume that every visual class in the design CSS is represented by a public component contract.
