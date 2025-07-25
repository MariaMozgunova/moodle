# core_ai (subsystem) Upgrade notes

## 5.1dev

### Added

- Error message handler for AI subsystem.
  - Object creation
    Use `core_ai\error\factory::create($errorcode, $reason, $errorsource)` to generate the appropriate error object.

  - Extensibility
    Add new error types by extending `core_ai\error\base` and registering them in the factory.
    Please see `core_ai\error\ratelimit` as an example.

  For more information see [MDL-83147](https://tracker.moodle.org/browse/MDL-83147)

### Changed

- The method `has_model_settings` inside `core_ai\aimodel\base` is now determined by values returned from a new method called `get_model_settings`.

  For more information see [MDL-84779](https://tracker.moodle.org/browse/MDL-84779)

## 5.0

### Added

- - A new hook, `\core_ai\hook\after_ai_action_settings_form_hook`, has been introduced. It will allows AI provider plugins to add additional form elements for action settings configuration.

  For more information see [MDL-82980](https://tracker.moodle.org/browse/MDL-82980)
- - AI provider plugins that want to implement `pre-defined models` and display additional settings for models must now extend the `\core_ai\aimodel\base` class.

  For more information see [MDL-82980](https://tracker.moodle.org/browse/MDL-82980)

### Changed

- - The `\core_ai\form\action_settings_form` class has been updated to automatically include action buttons such as Save and Cancel.
  - AI provider plugins should update their form classes by removing the `$this->add_action_buttons();` call, as it is no longer required.

  For more information see [MDL-82980](https://tracker.moodle.org/browse/MDL-82980)

### Deprecated

- The ai_provider_management_table has been refactored to inherit from flexible_table instead of plugin_management_table. As a result the methods get_plugintype and get_action_url are now unused and have been deprecated in the class.

  For more information see [MDL-82922](https://tracker.moodle.org/browse/MDL-82922)
