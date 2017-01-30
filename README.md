# WP CLI- Tips
WP-CLI tips and tricks

## Custom CSS

### Remove Custom CSS Post of all themes.
`wp post delete $(wp post list --post_type=custom_css --format=ids)`

### Remove Custom CSS Post of a theme.
`wp post delete $(wp post list --name=blue-planet --post_type=custom_css --format=ids)`

### Remove Custom CSS Post of currently active theme.
`wp post delete $(wp post list --name=$(wp option get stylesheet) --post_type=custom_css --format=ids)`
