:navigation-title: language-menu
..  include:: /Includes.rst.txt
..  _LanguageMenuProcessor:

============================
language-menu data processor
============================

The processor :php:`\TYPO3\CMS\Frontend\DataProcessing\LanguageMenuProcessor`,
alias `language-menu`, generates a list of language menu items which can be
assigned to the :typoscript:`FLUIDTEMPLATE` as a variable.

..  contents:: Table of contents

..  hint::
    The third-party extension
    `b13/menus <https://extensions.typo3.org/extension/menus>`__ also provides
    a language menu processor: :php:`B13\Menus\DataProcessing\LanguageMenu`.

    Refer to the `manual of the extension b13/menus
    <https://github.com/b13/menus/blob/master/README.md>`__ for more
    information.

..  _LanguageMenuProcessor-options:

Options:
========

..  confval-menu::
    :display: table
    :type:
    :Default:

    ..  _LanguageMenuProcessor-if:

    ..  confval:: if
        :name: LanguageMenuProcessor-if
        :Required: false
        :type: :ref:`if` condition

        Only if the condition is met the data processor is executed.

    ..  _LanguageMenuProcessor-languages:

    ..  confval:: languages
        :name: LanguageMenuProcessor-languages
        :Required: true
        :type: :ref:`data-type-string` / :ref:`stdWrap`
        :Default: "auto"
        :Example: "0,1,2"

        A list of comma-separated language IDs (e.g. 0,1,2) to use for the menu
        creation or `auto` to load from the :ref:`site configuration
        <t3coreapi:sitehandling>`.


    ..  _LanguageMenuProcessor-addQueryString-exclude:

    ..  confval:: addQueryString.exclude
        :name: LanguageMenuProcessor-addQueryString-exclude
        :Required: true
        :type: :ref:`data-type-string` / :ref:`stdWrap`
        :Default: ""
        :Example: "gclid,contrast"

        A list of comma-separated parameter names to be excluded from the language
        menu URLs.

    ..  _LanguageMenuProcessor-as:

    ..  confval:: as
        :name: LanguageMenuProcessor-as
        :Required: false
        :type: :ref:`data-type-string`
        :Default: defaults to the fieldName

        The variable name to be used in the Fluid template.

..  _LanguageMenuProcessor-example:

Example: Menu of all language from site configuration
=====================================================

Please see also :ref:`dataProcessing-about-examples`.

..  rubric:: TypoScript

Using the :php:`LanguageMenuProcessor` the following scenario is possible:

..  include:: /CodeSnippets/DataProcessing/TypoScript/LanguageMenuProcessor.rst.txt

..  rubric:: The Fluid template

This generated menu can be used in Fluid like this:

..  include:: /CodeSnippets/DataProcessing/Template/DataProcLangMenu.rst.txt

..  rubric:: Output

The array now contains information on all languages as defined in the site
configuration. As the current page is not translated into German, the
German language has the :php:`item.available` set to `false`. It therefore
does not get linked in the template.

..  include:: /Images/AutomaticScreenshots/DataProcessing/LanguageMenuProcessor.rst.txt
