i18n = import('i18n')

libexecdir_conf = configuration_data()
libexecdir_conf.set('libexecdir', prefix / libexecdir)

# Portal
adw_portal_interfaces = [
  'org.freedesktop.impl.portal.AppChooser',
  'org.freedesktop.impl.portal.FileChooser',
]
adw_portal_conf = configuration_data()
adw_portal_conf.set('PORTALS', ';'.join(adw_portal_interfaces))

portal_dir = datadir / 'xdg-desktop-portal' / 'portals'
configure_file(
  input: 'adw.portal.in',
  output: 'adw.portal',
  configuration: adw_portal_conf,
  install_dir: portal_dir,
)

# Service
configure_file(
  input: 'org.freedesktop.impl.portal.desktop.adw.service.in',
  output: 'org.freedesktop.impl.portal.desktop.adw.service',
  configuration: libexecdir_conf,
  install_dir: dbus_service_dir,
)

# systemd unit
if systemduserunitdir != ''
  configure_file(
    input: 'xdg-desktop-portal-adw.service.in',
    output: 'xdg-desktop-portal-adw.service',
    configuration: libexecdir_conf,
    install_dir: systemduserunitdir,
  )
endif

# Desktop file
desktop_in = configure_file(
  input: 'xdg-desktop-portal-adw.desktop.in.in',
  output: 'xdg-desktop-portal-adw.desktop.in',
  configuration: libexecdir_conf,
)

i18n.merge_file(
  type: 'desktop',
  input: desktop_in,
  output: 'xdg-desktop-portal-adw.desktop',
  po_dir: meson.project_source_root() / 'po',
  install: true,
  install_dir: datadir / 'applications',
)
