plugins = [
    'lrc123',
    'netease',
    'viewlyrics',
    'xiami',
]

foreach  plugin : plugins
    install_subdir (plugin, install_dir: join_paths(get_option('libdir'), 'lyricsources', 'plugins'))

    conf_data = configuration_data()
    conf_data.set('SERVICE_NAME', 'org.lyricsources.LyricSourcePlugin.'+plugin)
    conf_data.set('SERVICE_PATH', join_paths('plugins', plugin, plugin+'.py'))
    conf_data.set('PYTHON', find_program('python2').path())
    conf_data.set('PKGLIBDIR', join_paths(get_option('prefix'), get_option('libdir'), 'lyricsources'))

    configure_file (
        input: 'service.in',
        output: 'org.lyricsources.LyricSourcePlugin.'+plugin+'.service',
        configuration: conf_data,
        install_dir : join_paths(get_option('datadir'), 'dbus-1/services')
    )
endforeach
