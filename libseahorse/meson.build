marshaller = gnome.genmarshal('seahorse-marshal',
  sources: 'seahorse-marshal.list',
  prefix: 'seahorse_marshal',
)

search_provider_src = gnome.gdbus_codegen('seahorse-shell-search-provider-generated',
  'org.gnome.ShellSearchProvider2.xml',
  interface_prefix : 'org.gnome.',
  namespace : 'Seahorse',
)


libseahorse_sources = [
  'seahorse-application.c',
  'seahorse-bind.c',
  'seahorse-interaction.c',
  'seahorse-object-list.c',
  'seahorse-object-model.c',
  'seahorse-object-widget.c',
  'seahorse-progress.c',
  'seahorse-search-provider.c',
  'seahorse-util.c',
  'seahorse-widget.c',
  marshaller,
  resources_src,
  search_provider_src,
]

libseahorse_deps = [
  glib_deps,
  gcr,
  libsecret,
  libtreemultidnd_dep,
  common_dep,
]

libseahorse_lib = static_library('libseahorse',
  libseahorse_sources,
  dependencies: libseahorse_deps,
  include_directories: include_directories('..'),
)

libseahorse_dep = declare_dependency(
  link_with: libseahorse_lib,
)
