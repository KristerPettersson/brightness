    project('com.github.panosx2.brightness', 'vala', 'c')

    add_project_arguments(
        '-DGETTEXT_PACKAGE="@0@"'.format(meson.project_name()),
        language: 'c'
    )
    
    i18n = import('i18n')

    executable(
        meson.project_name(),
        'src/Dimmer.vala',
        dependencies: [
            dependency('gtk+-3.0'),
            dependency('gee-0.8')
        ],
        install: true
    )

    subdir('po')

    i18n.merge_file(
        input: join_paths('data', meson.project_name() + '.desktop.in'),
        output: meson.project_name() + '.desktop',
        po_dir: join_paths(meson.source_root(), 'po'),
        type: 'desktop',
        install: true,
        install_dir: join_paths(get_option('datadir'), 'applications')
    )

    i18n.merge_file(
        input: join_paths('data', meson.project_name() + '.appdata.xml.in'),
        output: meson.project_name() + '.appdata.xml',
        po_dir: join_paths(meson.source_root(), 'po'),
        install: true,
        install_dir: join_paths(get_option('datadir'), 'metainfo')
    )

    icon_sizes = ['16', '24', '32', '48', '64', '128']

    foreach i : icon_sizes
        install_data(
            join_paths('icons', i, meson.project_name() + '.png'),
            install_dir: join_paths(get_option('datadir'), 'icons', 'hicolor', i + 'x' + i, 'apps')
        )
    endforeach
