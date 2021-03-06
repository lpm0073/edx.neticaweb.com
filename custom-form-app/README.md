# Open edX Custom Registration Form fields
## Django App

1. Install with `pip install -e .` within this folder within the edx platform virtual environment.
2. Add "custom_reg_form" to the "ADDL_INSTALLED_APPS" array in `lms.env.json` (you may have to create it if it doesn't exist.)
3. Set "REGISTRATION_EXTENSION_FORM" to "custom_reg_form.forms.ExtraInfoForm" in `lms.env.json`.
4. Run migrations.
5. Start/restart the LMS.


## Adding Custom Fields to the Registration Page

This topic describes how to add custom fields to the registration page for your
instance of Open edX.

### Overview

By default, the registration page for each instance of Open edX has fields that
ask for information such as a user's name, country, and highest level of
education completed. You can add custom fields to the registration page for
your own Open edX instance. These fields can be different types, including
text entry fields and drop-down lists.

### Add Custom Fields to the Registration Page

Before you add a custom field to the registration page, you must make sure that
the combined sign-in and registration form is enabled for your Open edX
instance. To do this, open the ``lms.env.json`` and ``cms.env.json`` files, and
set the ``ENABLE_COMBINED_LOGIN_REGISTRATION`` feature flag to True. These
files are located one level above the ``edx- platform`` directory.

To add custom fields to the registration page, follow these steps.

1. :ref:`Start the LMS<Start the LMS>` and sign in to your instance of Open edX.

2. Use Python to create a Django form that contains the fields that you want to
   add to the page, and then create a Django model to store the information
   from the form.

   For more information about how to create Django forms, see `Django Forms`_
   on the `Django website`

3. In the ``lms.env.json`` file, add the app for your model to the
   ``ADDL_INSTALLED_APPS`` array.

4. In the ``lms.env.json`` file, set the ``REGISTRATION_EXTENSION_FORM``
   setting to the path of the Django form that you just created, as a dot-
   separated Python string.

   For example, if your form is named "ExampleExtensionForm" and is located at
   "path/to/the_form.py", the value of the setting is
   ``path.to.the_form.ExampleExtensionForm``.

5. Run database migrations.

6. Restart the LMS and verify that the new fields appear on your registration
   form.
