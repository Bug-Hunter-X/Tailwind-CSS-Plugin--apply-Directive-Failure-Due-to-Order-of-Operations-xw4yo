# Tailwind CSS Plugin @apply Directive Failure

This repository demonstrates a bug related to using the `@apply` directive within a Tailwind CSS plugin. The issue arises from the order in which the plugin and the base Tailwind styles are processed.  If the plugin references styles that haven't been compiled yet, the `@apply` directive fails.

## Bug Description
The problem occurs when the `@apply` directive in a plugin tries to utilize styles that are defined later in the Tailwind CSS compilation process.  This leads to missing styles in the final output.

## Solution
The bug is resolved by ensuring that the plugin's `addUtilities` or `addComponents` function only applies styles after all of Tailwind's core styles have been compiled.  In practice, this often involves tweaking the plugin's load order or restructuring the way styles are defined.