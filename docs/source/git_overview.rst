Git Repository Data Extraction
===============================

The ``tidyextractors.tidygit`` submodule lets you extract Git log data from a local Git repository. This page will guide you through the process.

Step 1: Prepare Your Git Repo
----------------------------------

All you need to get started is the path to any local Git repository. If you want to extract data from a repository hosted on GitHub, download or clone the repository to your computer.

Step 2: Extract Data
-------------------------

You can extract data from any local Git repository using the ``GitExtractor``:

.. code-block:: python

  import tidyextractors.tidygit as tg

  gx = tg.GitExtractor('./your/repo/dir/')


Step 3: Get Data
--------------------------

You can now get your data in a number of tidy formats using either the ``get_tidy`` method:

.. code-block:: python

  commits_df = gx.get_tidy('commits')

  changes_df = gx.get_tidy('changes')

A slightly my flexible option is to call the ``GitExtractor`` output methods directly. This is useful if you want to include collections in the cells of your DataFrame (e.g. lists or dictionaries), which are dropped when using ``get_tidy`` because tidy data must have only atomic values.

.. code-block:: python

  commits_df = gx.commits()

  changes_df = gx.changes()

``get_tidy`` Options and Aliases
----------------------------------

As shown above, there are two format options for ``GitExtractor.get_tidy``. Each of these options may also use a short alias:

+---------+-------------+----------------------------------+
| Lookup  | Method Used | Example Usage                    |
+=========+=============+==================================+
| commits | commits     | GitExtractor.get_tidy('commits') |
+---------+-------------+----------------------------------+
| changes | changes     | GitExtractor.get_tidy('changes') |
+---------+-------------+----------------------------------+
| cm      | commits     | GitExtractor.get_tidy('cm')      |
+---------+-------------+----------------------------------+
| ch      | changes     | GitExtractor.get_tidy('ch')      |
+---------+-------------+----------------------------------+