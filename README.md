# WP CLI- Tips
WP-CLI tips and tricks

## Comments

### Empty trash.
`wp comment delete $(wp comment list --status=trash --format=ids)`

### Delete all spam comments.
`wp comment delete $(wp comment list --status=spam --format=ids)`

### Mark all pending comments as spam.
`wp comment spam $(wp comment list --status=hold --format=ids)`

## Custom CSS

### Remove Custom CSS Post of all themes.
`wp post delete $(wp post list --post_type=custom_css --format=ids)`

### Remove Custom CSS Post of a theme.
`wp post delete $(wp post list --name=blue-planet --post_type=custom_css --format=ids)`

### Remove Custom CSS Post of currently active theme.
`wp post delete $(wp post list --name=$(wp option get stylesheet) --post_type=custom_css --format=ids)`

