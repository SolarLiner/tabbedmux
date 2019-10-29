project('tabbedmux', 'vala', 'c', version: '1.24')

add_project_arguments(
	'--target-glib=2.38',
	'--vapidir', meson.current_source_dir() / 'vapis',
	'--vapidir', meson.current_source_dir() / '.',
	'--pkg', 'version',
	'--pkg', 'tcpmisc'
, language: 'vala')

gnome = import('gnome')

src = files(
	'application.vala',
	'contextmenu.vala',
	'keyboard_interactive.vala',
	'misc.c',
	'open.vala',
	'password_adapter.c',
	'saved_sessions.vala',
	'tabbedmux.vala',
	'terminal.vala',
	'tmux_decode.c',
	'tmux_decode.vapi',
	'tmux_local.vala',
	'tmux_manager.vala',
	'tmux_ssh.vala',
	'util.vala',
	'window.vala',
)

deps = [
	dependency('gee-0.8'),
	dependency('gio-unix-2.0'),
	dependency('gtk+-3.0'),
	dependency('libnotify'),
	dependency('libssh2'),
	dependency('vte-2.91'),
]

resources_c = gnome.compile_resources('tabbedmux', files('resources.xml'), '.')
version_h = configure_file(
	output: 'version.h',
	configuration: {
		'TABBED_MUX_VERSION': meson.project_version()
	}
)

install_data(files('name.masella.tabbedmux.gschema.xml'), install_dir: 'share/glib-2.0/schemas')
install_data(files('tabbedmux.desktop'), install_dir: 'share/applications')
meson.add_install_script('build-aux/compile_schemas.sh')

exe = executable(meson.project_name(), src, resources_c, dependencies: deps, install: true)
