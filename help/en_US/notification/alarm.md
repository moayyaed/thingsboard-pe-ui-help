#### Alarm notification templatization

<div class="divider"></div>
<br/>

Notification subject, message and button support templatization and localization.
The list of available templatization parameters depends on the template type.
See the available types and parameters below:

Available template parameters:

* `alarmType` - alarm type;
* `action` - one of: 'created', 'severity changed', 'acknowledged', 'cleared', 'deleted';
* `alarmId` - the alarm id as uuid string;
* `alarmSeverity` - alarm severity (lower case);
* `alarmStatus` - the alarm status;
* `alarmOriginatorEntityType` - the entity type of the alarm originator, e.g. 'Device';
* `alarmOriginatorName` - the name of the alarm originator, e.g. 'Sensor T1';
* `alarmOriginatorId` - the alarm originator entity id as uuid string;
* `recipientTitle` - title of the recipient (first and last name if specified, email otherwise);
* `recipientEmail` - email of the recipient;
* `recipientFirstName` - first name of the recipient;
* `recipientLastName` - last name of the recipient;

Parameter names must be wrapped using `${...}`. For example: `${action}`.
You may also modify the value of the parameter with one of the suffixes:

* `upperCase`, for example - `${recipientFirstName:upperCase}`
* `lowerCase`, for example - `${recipientFirstName:lowerCase}`
* `capitalize`, for example - `${recipientFirstName:capitalize}`

To localize the notification, use `translate` suffix: `${some.translation.key:translate}`

For example, if you have a custom translation key `custom.notifications.greetings` with value `Hello, ${recipientFirstName}!`, the template
`${custom.notifications.greetings:translate}` will be transformed to `Hello, John!`. 
The needed locale is taken from recipient's profile settings, using English by default.


<div class="divider"></div>

##### Examples

Let's assume the notification about new alarm with type 'High Temperature' for device 'Sensor A'. 
The following template:

```text
Alarm '${alarmType}' - ${action:upperCase}
{:copy-code}
```

will be transformed to:

```text
Alarm 'High Temperature' - CREATED
```

<br/>

The following template:

```text
${alarmOriginatorEntityType:capitalize} '${alarmOriginatorName}'
{:copy-code}
```

will be transformed to:

```text
Device - Sensor A
```

<br>
<br>
