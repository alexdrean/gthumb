
source_files = files(
  'actions.c',
  'callbacks.c',
  'dlg-export-to-facebook.c',
  'facebook-album.c',
  'facebook-album-properties-dialog.c',
  'facebook-photo.c',
  'facebook-service.c',
  'main.c'
)

shared_module('facebook',
  sources : source_files,
  dependencies : [
    extension_common_deps,
    importer_dep,
    libsoup_dep,
    libjson_glib_dep,
    webkit2_dep,
    use_libsecret ? libsecret_dep : [],
  ],
  include_directories : [
    config_inc,
    gthumb_inc,
    importer_inc
  ],
  c_args : c_args,
  link_with : [
    oauth_mod,
    export_tools_mod,
    photo_importer_mod,
    importer_mod
  ],
  install : true,
  install_dir : extensions_install_dir,
  install_rpath : extensions_install_dir
)

# .extension file

extension_in_file = configure_file(
  input : 'facebook.extension.desktop.in.in',
  output : 'facebook.extension.in',
  configuration : extension_data
)

i18n.merge_file(
  input : extension_in_file,
  output : 'facebook.extension',
  type : 'desktop',
  po_dir : po_dir,
  install : true,
  install_dir : extensions_install_dir
)

# Subdirectories

subdir('data')
