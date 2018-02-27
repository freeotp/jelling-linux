project('jelling', 'c')

libexecdir = join_paths(get_option('prefix'), get_option('libexecdir'))

libsystemd = dependency('libsystemd', version: '>=221')
systemd = dependency('systemd', version: '>=221')
bluez = dependency('bluez', version: '>=5.42')

unitdir = systemd.get_pkgconfig_variable('systemdsystemunitdir')
modsdir = systemd.get_pkgconfig_variable('modulesloaddir')

config = configuration_data()
config.set('libexecdir', libexecdir)
configure_file(
    input: 'jelling.service.in',
    output: 'jelling.service',
    configuration: config,
    install_dir: unitdir
)

install_data(
    sources: 'jelling.conf',
    install_dir: modsdir
)

executable(
    'jelling',
    'jelling.c',
    install_dir : libexecdir,
    dependencies: libsystemd,
    install: true,
    c_args: [
        '-Wall',
        '-Wextra',
        '-Werror',
        '-Wstrict-aliasing',
        '-Wchar-subscripts',
        '-Wformat-security',
        '-Wmissing-declarations',
        '-Wmissing-prototypes',
        '-Wnested-externs',
        '-Wpointer-arith',
        '-Wshadow',
        '-Wsign-compare',
        '-Wstrict-prototypes',
        '-Wtype-limits',
        '-Wunused-function',
        '-Wno-missing-field-initializers',
        '-Wno-unused-parameter',
    ]
)
