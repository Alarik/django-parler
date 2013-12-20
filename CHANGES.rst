Changes in version 1.0 (in development)
---------------------------------------

* **BACKWARDS INCOMPATIBLE:** updated the model name of the dynamically generated translation models for django-hvad_ compatibility.
  This only affects your South migrations. Use ``manage.py schemamigration appname --empty "upgrade_to_django_parler10"`` to upgrade
  applications which use ``translations = TranslatedFields(..)`` in their models.
* Fix supporting different database (using=) arguments.
* Fix list language, always show translated values.
* Fix ``is_supported_django_language()`` to support dashes too


Changes in version 0.9.4 (beta)
-------------------------------

* Added support for inlines!
* Fix error in Django 1.4 with "Save and continue" button on add view.
* Fix error in ``save_translations()`` when objects fetched fallback languages.
* Add ``save_translation(translation)`` method, to easily hook into the ``translation.save()`` call.
* Added support for empty ``translations = TranslatedFields()`` declaration.


Changes in version 0.9.3 (beta)
-------------------------------

* Support using ``TranslatedFieldsModel`` with abstract models.
* Added ``parler.appsettings.add_default_language_settings()`` function.
* Added ``TranslatableManager.queryset_class`` attribute to easily customize the queryset class.
* Added ``TranslatableManager.translated()`` method to filter models with a specific translation.
* Added ``TranslatableManager.active_translations()`` method to filter models which should be displayed.
* Added ``TranslatableAdmin.get_form_language()`` to access the currently active language.
* Added ``hide_untranslated`` option to the ``PARLER_LANGUAGES`` setting.
* Added support for ``ModelAdmin.formfield_overrides``.


Changes in version 0.9.2 (beta)
-------------------------------

* Added ``TranslatedField(any_language=True)`` option, which uses any language as fallback
  in case the currently active language is not available. This is ideally suited for object titles.
* Improved ``TranslationDoesNotExist`` exception, now inherits from ``AttributeError``.
  This missing translations fail silently in templates (e.g. admin list template)..
* Added unittests
* Fixed Django 1.4 compatibility
* Fixed saving all translations, not only the active one.
* Fix sending ``pre_translation_save`` signal.
* Fix passing ``_current_language`` to the model __init__ function.


Changes in version 0.9.1 (beta)
-------------------------------

* Added signals to detect translation model init/save/delete operations.
* Added default ``TranslatedFieldsModel`` ``verbose_name``, to improve the delete view.
* Allow using the ``TranslatableAdmin`` for non-``TranslatableModel`` objects (operate as NO-OP).


Changes in version 0.9 (beta)
-----------------------------

* First version, based on intermediate work in django-fluent-pages_.
  Integrating django-hvad_ turned out to be very complex, hence this app was developped instead.


.. _django-fluent-pages: https://github.com/edoburu/django-fluent-pages
.. _django-hvad: https://github.com/kristianoellegaard/django-hvad
