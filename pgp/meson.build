pgp_sources = [
  'seahorse-combo-keys.c',
  'seahorse-discovery.c',
  'seahorse-gpgme.c',
  'seahorse-gpgme-add-subkey.c',
  'seahorse-gpgme-add-uid.c',
  'seahorse-gpgme-data.c',
  'seahorse-gpgme-expires.c',
  'seahorse-gpgme-exporter.c',
  'seahorse-gpgme-generate.c',
  'seahorse-gpgme-key.c',
  'seahorse-gpgme-key-deleter.c',
  'seahorse-gpgme-key-op.c',
  'seahorse-gpgme-keyring.c',
  'seahorse-gpgme-photo.c',
  'seahorse-gpgme-photos.c',
  'seahorse-gpgme-revoke.c',
  'seahorse-gpgme-secret-deleter.c',
  'seahorse-gpgme-sign.c',
  'seahorse-gpgme-subkey.c',
  'seahorse-gpgme-uid.c',
  'seahorse-gpg-op.c',
  'seahorse-gpg-options.c',
  'seahorse-pgp.c',
  'seahorse-pgp-actions.c',
  'seahorse-pgp-backend.c',
  'seahorse-pgp-key.c',
  'seahorse-pgp-key-properties.c',
  'seahorse-pgp-keysets.c',
  'seahorse-pgp-photo.c',
  'seahorse-pgp-signature.c',
  'seahorse-pgp-subkey.c',
  'seahorse-pgp-uid.c',
  'seahorse-signer.c',
  'seahorse-transfer.c',
  'seahorse-unknown.c',
  'seahorse-unknown-source.c',
]

pgp_dependencies = [
  glib_deps,
  gcr,
  gpgme,
  common_dep,
]

pgp_c_flags = [
]

if with_ldap
  pgp_sources += 'seahorse-ldap-source.c'
  pgp_dependencies += [
    libldap,
    liblber,
  ]
  pgp_c_flags += '-DLDAP_DEPRECATED'
endif

if with_hkp
  pgp_sources += 'seahorse-hkp-source.c'
  pgp_dependencies += libsoup
endif

if with_keyservers
  pgp_sources += [
    'seahorse-server-source.c',
    'seahorse-keyserver-search.c',
    'seahorse-keyserver-sync.c',
    'seahorse-keyserver-results.c',
  ]
endif

if with_key_sharing
  pgp_dependencies += [
    avahi_client,
    avahi_glib,
  ]
endif

pgp_lib = static_library('seahorse-pgp',
  pgp_sources,
  dependencies: pgp_dependencies,
  c_args: pgp_c_flags,
)

pgp_dep = declare_dependency(
  link_with: pgp_lib,
  include_directories: include_directories('.'),
)

# xloadimage helper binary
xloadimage = executable('xloadimage',
  'seahorse-xloadimage.c',
  install: true,
  install_dir: libexecbindir,
)
