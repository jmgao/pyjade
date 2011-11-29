======
PyJade
======

PyJade is a high performance template preprocessor, that converts any .jade source to the each Template-language (Django, Jinja2 or Mako).


INSTALLATION
============

First, you must do::

	pip install pyjade

Or::

	wget https://github.com/SyrusAkbary/pyjade/zipball/master
	unzip SyrusAkbary-pyjade-*
	cd SyrusAkbary-pyjade-*
	python setup.py install

Now simply **name your templates with a `.jade` extension** and this jade compiler
will do the rest.  Any templates with other extensions will not be compiled
with the pyjade compiler.


Django
------

In `settings.py`, modify `TEMPLATE_LOADERS` like::

    TEMPLATE_LOADERS = (
        'pyjade.django.FSLoader',
        'pyjade.django.AppLoader',
    )

These replace your usual Django loaders::

    django.template.loaders.filesystem.Loader
    django.template.loaders.app_directories.Loader


Jinja2
------

Just add `pyjade.ext.jinja.PyJadeExtension` as extension::

    jinja_env = Environment(extensions=['pyjade.ext.jinja.PyJadeExtension'])


Mako
----

Just add  `pyjade.ext.mako.preprocessor` as preprocessor::

    from pyjade.ext.mako import preprocessor as mako_preprocessor
    mako.template.Template(haml_source,
        preprocessor=mako_preprocessor
    )

**Actually the mako preprocessor is in development mode**

Flask
-----

Just add  `pyjade.ext.jinja.PyJadeExtension` as extension to the environment of the app::

	app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')


Pyramid
-------

Adjust your "your_project/__init__.py" and add the following line somewhere to in the main() function::

	config.include('pyjade.ext.pyramid')


Syntax
======

The same as the Jade Node.js module
https://github.com/visionmedia/jade/blob/master/Readme.md


TODOs and BUGS
==============
See: http://github.com/syrusakbary/pyjade/issues