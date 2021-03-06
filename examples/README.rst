Sample Gallery
==============

This is an example gallery that demonstrates how to use PyVista with
`sphinx-gallery <https://sphinx-gallery.github.io/>`_.

Enable this in your ``conf.py`` by adding:

.. code:: python

    # -- PyVista Configuration for the Gallery-------------------------------------

    from sphinx_gallery.sorting import FileNameSortKey
    import pyvista

    # Manage errors
    pyvista.set_error_output_file("errors.txt")
    # Ensure that offscreen rendering is used for docs generation
    pyvista.OFF_SCREEN = True  # Not necessary - simply an insurance policy
    # Preferred plotting style for documentation
    pyvista.set_plot_theme("document")
    pyvista.global_theme.window_size = [1024, 768]
    pyvista.global_theme.font.size = 22
    pyvista.global_theme.font.label_size = 22
    pyvista.global_theme.font.title_size = 22
    pyvista.global_theme.return_cpos = False
    pyvista.set_jupyter_backend(None)

    # Save figures in specified directory
    pyvista.FIGURE_PATH = os.path.join(os.path.abspath("./images/"), "auto-generated/")
    if not os.path.exists(pyvista.FIGURE_PATH):
        os.makedirs(pyvista.FIGURE_PATH)

    # necessary when building the sphinx gallery
    pyvista.BUILDING_GALLERY = True
    os.environ["PYVISTA_BUILDING_GALLERY"] = "true"

    extensions = [
        # ... other extensions
        "sphinx_gallery.gen_gallery",
    ]


    sphinx_gallery_conf = {
        # convert rst to md for ipynb
        "pypandoc": True,
        # path to your examples scripts
        "examples_dirs": "../examples",
        # path where to save gallery generated examples
        "gallery_dirs": "gallery",
        "filename_pattern": r"\.py",
        # Remove the 'Download all examples' button from the top level gallery
        "download_all_examples": False,
        # Remove sphinx configuration comments from code blocks
        "remove_config_comments": True,
        # Sort gallery example by file name instead of number of lines (default)
        "within_subsection_order": FileNameSortKey,
        # directory where function granular galleries are stored
        "backreferences_dir": None,
        # Modules for which function level galleries are created.  In
        "doc_module": "pyvista",
        "image_scrapers": ("pyvista", "matplotlib"),
        "first_notebook_cell": "%matplotlib inline\n"
        "from pyvista import set_plot_theme\n"
        'set_plot_theme("document")\n',
    }


Read more about configuring sphinx gallery at `sphinx-gallery Configuration
<https://sphinx-gallery.github.io/dev/configuration.html#image-scrapers>`_


Examples
--------

..
   This will be populated by sphinx...
