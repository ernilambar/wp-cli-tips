# WP CLI- Tips
WP-CLI tips and tricks

### Comments

##### Empty trash.
`wp comment delete $(wp comment list --status=trash --format=ids)`

##### Delete all spam comments.
`wp comment delete $(wp comment list --status=spam --format=ids)`

##### Mark all pending comments as spam.
`wp comment spam $(wp comment list --status=hold --format=ids)`

### Media

##### Regenerate all thumbnails that have attachment IDs between 1000 and 2000.
`seq 1000 2000 | xargs wp media regenerate`

##### Regenerate all thumbnails that are set as Featured Image in pages.
`wp media regenerate $(wp post list --post_type=page --format=ids | xargs -d ' ' -I % wp db query 'SELECT meta_value FROM wp_postmeta WHERE post_id=% AND meta_key="_thumbnail_id"' --skip-column-names)`

##### Import all jpgs in the current user's "Pictures" folder.
`wp media import ~/Pictures/**\/*.jpg`

##### Import a local image and set it to be the post thumbnail for a post.
`wp media import ~/Pictures/himalaya.jpg --post_id=123 --title="Himalaya range" --featured_image`

### Custom CSS

##### Remove Custom CSS Post of all themes.
`wp post delete $(wp post list --post_type=custom_css --format=ids)`

##### Remove Custom CSS Post of a theme.
`wp post delete $(wp post list --name=blue-planet --post_type=custom_css --format=ids)`

##### Remove Custom CSS Post of currently active theme.
`wp post delete $(wp post list --name=$(wp option get stylesheet) --post_type=custom_css --format=ids)`

### Options

##### Delete all options begining with "theme_mods_".
`wp option list --search="theme_mods_*" --field=option_name | xargs -I % wp option delete %`

##### Delete all widget instances.
`wp option list --search="widget_*" --field=option_name | xargs -I % wp option delete %`

### Widgets

##### Delete all inactive widgets.
`wp widget delete $(wp widget list wp_inactive_widgets --format=ids)`

##### Move all widgets from "sidebar-1" to "sidebar-2".
`wp widget list sidebar-1 --format=ids | xargs -d ' ' -I % wp widget move % --sidebar-id=sidebar-2`
