# Using Prospects


## [](#supported-operations-a-name-supported-operations-id-supported-operations-a-)Supported Operations<a name="14833-supported-operations" id="supported-operations"></a>

For a complete list of fields involved in Prospect operations, see the [Prospect](../object-field-references#prospect) section of [Object Field References](../object-field-references).

Note: Prospect email addresses cannot be updated using this method.

| **Operation** | **URL Format**   | **Required Parameters** | **Description**  |
| ------------- | ---------------- | ----------------------- | -----------------|
| `assign`      | `/api/prospect /version/3 /do/assign/ email/**__**?...` | `user_key, api_key, email, (user_email OR user_id OR group_id)` | Assigns or reassigns the prospect specified by `<email>` to a specified Pardot user or group. One (and only one) of the following parameters must be provided to identify the target user or group: `<user_email>`, `<user_id>`, or `<group_id>`. Returns an updated version of the prospect. **_Note:_** Prospect assignments and reassignments do not overwrite existing assignments in CRMs. |
| `assign`      | `/api/prospect /version/3 /do/assign/ id/**__**?...` | `user_key, api_key, id, (user_email OR user_id OR group_id)` | Assigns or reassigns the prospect specified by `<id>` to a specified Pardot user or group. One (and only one) of the following parameters must be provided to identify the target user or group: `<user_email>`, `<user_id>`, or `<group_id>`. Returns an updated version of the prospect. **_Note:_** Prospect assignments and reassignments do not overwrite existing assignments in CRMs. |
| `unassign`        | `/api/prospect /version/3 /do/unassign/ email/**__**?...` | `user_key, api_key, email` | Unassigns the prospect specified by `<email>`. Returns an updated version of the prospect. **_Note:_**Prospect assignments and reassignments do not overwrite existing assignments in CRMs. **_Note:_** Prospect assignments and reassignments do not overwrite existing assignments in CRMs. |
| `unassign`   | `/api/prospect /version/3 /do/unassign/ id/**__**?...`   | `user_key, api_key, id` | Unassigns the prospect specified by `<id>`. Returns an updated version of the prospect. **_Note:_** Prospect assignments and reassignments do not overwrite existing assignments in CRMs. **_Note:_** Prospect assignments and reassignments do not overwrite existing assignments in CRMs. |
| `create`   | `/api/prospect /version/3 /do/create/ email/**__**?...` | `user_key, api_key, email` | Creates a new prospect using the specified data. `<email>` must be a unique email address. Email list subscriptions and custom field data may also be added with this request. Refer to the [Updating Email List Subscriptions](#updating-email-list-subscriptions) and [Updating Field Values](#14833-updating-field-values) sections for more details.
| `read` | `/api/prospect /version/3 /do/read/ email/**__**?...` | `user_key, api_key, email` | Returns data for the prospect specified by `<email>`, including campaign assignment, profile criteria matching statuses, associated visitor activities, email list subscriptions, and custom field data. `` is the email address of the target prospect. |
| `read`      | `/api/prospect /version/3 /do/read/ id/**__**?...` | `user_key, api_key, id` | Returns data for the prospect specified by `<id>`, including campaign assignment, profile criteria matching statuses, associated visitor activities, email list subscriptions, and custom field data. `` is the Pardot ID of the target prospect. |
| `update`      | `/api/prospect /version/3 /do/update/ email/**__**?...` | `user_key, api_key, email` | Updates the provided data for a prospect specified by `<email>`. `<email>` is the email address of the prospect. Fields that are not updated by the request remain unchanged. Email list subscriptions and custom field data may also be updated with this request. Refer to the [Updating Email List Subscriptions](#updating-email-list-subscriptions) and [Updating Field Values](#14833-updating-field-values) sections for more details. Returns an updated version of the prospect. **_Note:_** Prospect email addresses cannot be updated using this method. |
| `update`        | `/api/prospect /version/3 /do/update/ id/**__**?...` | `user_key, api_key, id` | Updates the provided data for a prospect specified by `<id>`. `<id>` is the Pardot ID of the prospect. Fields that are not updated by the request remain unchanged. Email list subscriptions and custom field data may also be updated with this request. Refer to the [Updating Email List Subscriptions](#updating-email-list-subscriptions) and [Updating Field Values](#14833-updating-field-values) sections for more details. Returns an updated version of the prospect. |
| `upsert`   | `/api/prospect /version/3 /do/upsert/ email/**__**?...`   | `user_key, api_key, email` | Updates the provided data for the prospect specified by `<email>`. If a prospect with the provided email address does not yet exist, a new prospect is created using the `<email>` value. Fields that are not updated by the request remain unchanged. Email list subscriptions and custom field data may also be updated with this request. Refer to the [Updating Email List Subscriptions](#14833-updating-email-list-subscriptions) and [Updating Field Values](#14833-updating-field-values) sections for more details. Returns an updated version of the prospect. |
| `upsert`   | `/api/prospect /version/3 /do/upsert/ id/**__**?...` | `user_key, api_key, (id OR email)` | Updates the provided data for the prospect specified by `<id>`. If an `<email>` value is provided, it is used to update the prospect's email address. If a prospect with the provided ID is not found, Pardot searches for a prospect identified by `<email>`. If a prospect with the provided email address does not yet exist, a new prospect is created using `<email>` value. Fields that are not updated by the request remain unchanged. Email list subscriptions and custom field data may also be updated with this request. Refer to the [Updating Email List Subscriptions](#updating-email-list-subscriptions) and [Updating Field Values](#14833-updating-field-values) sections for more details. Returns an updated version of the prospect.
| `delete` | `/api/prospect /version/3 /do/delete/ email/**__**?...` | `user_key, api_key, email` | Deletes the prospect specified by `<email>`. Returns HTTP 204 No Content on success. **_Note:_** Prospects may only be deleted using HTTP methods POST or DELETE. |
| `delete` | `/api/prospect /version/3 /do/delete/ id/**__**?...` | `user_key, api_key, id` | Deletes the prospect specified by `<id>`. Returns HTTP 204 No Content on success. **_Note:_** Prospects may only be deleted using HTTP methods POST or DELETE. |



<a name="14833-xml-response-formats" id="xml-response-formats"></a>

## [](#xml-response-formats-)XML Response Formats

For `output=full`:

```
<rsp stat="ok" version="1.0">
    <prospect>
        ...
        <campaign>
            ...
        </campaign>
        <assigned_to>
            ...
        </assigned_to>
        <last_activity>
            ...
        </last_activity>
        <profile>
            ...
            <profile_criteria>
                ...
            </profile_criteria>
        </profile>
        <visitors>
            <visitor>
                ...
                <identified_company>
                    ...
                </identified_company>
                <visitor_referrer>
                    ...
                </visitor_referrer>
            </visitor>
        </visitors>
        <visitor_activities>
            <visitor_activity>
                ...
            </visitor_activity>
        </visitor_activities>
        <lists>
            <list_subscription>
                ...
                <list>
                    ...
                </list>
            </list_subscription>
        </lists>
    </prospect>
</rsp>
```

For `output=simple`:

```
<rsp stat="ok" version="1.0">
    <prospect>
        ...
        <campaign>
            ...
        </campaign>
        <assigned_to>
            ...
        </assigned_to>
        <last_activity>
            ...
        </last_activity>
    </prospect>
</rsp>
```

For `output=mobile`:

```
<rsp stat="ok" version="1.0">
    <prospect>
        <id>...</id>
        <first_name>...</first_name>
        <last_name>...</last_name>
        <email>...</email>
        <company>...</company>
    </prospect>
</rsp>
```
| **Tag**                    | **Description** |
|----------------------------|-----------------|
| `<prospect>`            | Parent tag. Contains data fields for the target prospect (including custom fields). For complete field listing, see [Prospect](../object-field-references#prospect) in [Object Field References](../object-field-references). |
| `<value>`               | Child tag of data fields with multiple values. Only appears with custom fields that have multiple values.|
| `<campaign>` | Contains `<id>` and `<name>` of the campaign to which this prospect has been assigned. This leaf only appears if the prospect has been assigned to a campaign. |
| `<assigned_to>` | Contains a `<user>` node detailing the user to whom this prospect has been assigned. This leaf only appears if the prospect has been assigned to a user. See [User](../object-field-references#user) in [Object Field References](../object-field-references). |
| `<last_activity>` | Contains a `<visitor_activity>` node detailing this prospect's most recent activity. This leaf only appears if the prospect has visitor activities associated with it. For complete field listing, see [Visitor Activity](../object-field-references#visitor-activity) in [Object Field References](../object-field-references). |
| `<profile>` | Contains all data fields for the profile associated with this prospect. Also contains several `<profile_criteria>` tags. For complete field listing, see [Profile](../object-field-references#profile) in [Object Field References.](../object-field-references) |
| `<profile_criteria>` | Contains all data fields for the profile criteria associated with the prospect's assigned profile. For complete field listing, see [Profile Criteria](../object-field-references#profile-criteria) in [Object Field References](../object-field-references). |
| `<visitors>` | Contains all visitors associated with this prospect. Contains only `<visitor>` tags. |
| `<visitor>` | Contains data fields for a visitor activity, as well as an `<identified_company>` and a `<visitor_referrer>` tag. For complete field listing, see [Visitor](../object-field-references#visitor) in [Object Field References](../object-field-references). |
| `<identified_company>` | Contains data field for a visitor's identified company. For complete field listing, see [Identified Company](../object-field-references#identified-company) in [Object Field References](../object-field-references). |
| `<visitor_referrer>` | Contains data fields for a visitor's referrer. For complete field listing, see [Visitor Referrer](../object-field-references#visitor-referrer) in [Object Field References](../object-field-references). |
| `<visitor_activities>` | Contains all visitor activities associated with this prospect. Contains only `<visitor_activity>` tags. |
| `<visitor_activity>` | Contains data fields for a visitor activity. For complete field listing, see [Visitor Activity](../object-field-references#visitor-activity) in [Object Field References](../object-field-references). |
| `<lists>` | Contains all email list subscriptions for this prospect. Contains only `<list_subscription>` tags. |
| `<list_subscription>` | Contains data fields for an email list subscription, as well as a `<list>` tag. For complete field listing, see [Email List Subscription](../object-field-references#email-list-subscription) in [Object Field References](../object-field-references). |
| `<list>` | Contains data fields for an email list. For complete field listing, see [Email List](../object-field-references#email-list) in [Object Field References](.. object-field-references). |

<a name="14833-assigning-and-reassigning-prospects" id="assigning-and-reassigning-prospects"></a>

## [](#assigning-and-reassigning-prospects-)Assigning and Reassigning Prospects

To assign/reassign a prospect, both the prospect to be assigned and the target user or group of the assignment must be defined. Prospects can be specified by their Pardot ID or email address. Users or groups can be specified by their Pardot user ID, email address, or Pardot group ID. Possible combinations of parameters are shown below. Developers are responsible for substituting specific values for parameters denoted by `<carets>`.

**_Examples:_**

/api/prospect/version/3/do/assign/email/?user_email=&amp;api_key=&amp;user_key=
/api/prospect/version/3/do/assign/email/?user_id=&amp;api_key=&amp;user_key=
/api/prospect/version/3/do/assign/email/?group_id=&amp;api_key=&amp;user_key=
/api/prospect/version/3/do/assign/id/?user_email=&amp;api_key=&amp;user_key=
/api/prospect/version/3/do/assign/id/?user_id=&amp;api_key=&amp;user_key=
/api/prospect/version/3/do/assign/id/?group_id=&amp;api_key=&amp;user_key=

XML responses to `assign` requests are identical to `read` requests, but reflect the new prospect assignment in the `<assigned_to>` node.

<a name="14833-creating-prospects" id="creating-prospects"></a>

## [](#creating-prospects-)Creating Prospects

To create a prospect via the API, only a valid and unique email address is required. Values for any other prospect fields may also be provided in the `create` request. Developers are responsible for substituting specific values for parameters denoted by `<carets>`.

_**Example:** Creating a new prospect_/api/prospect/version/3/do/create/email/[new_prospect@pardot.com](mailto:new_prospect@pardot.com)?first_name=New&amp;last_name=Prospect&amp;api_key=&amp;user_key=

XML responses to `create` requests are identical to `update` and `read` requests. If no `campaign_id` value is provided, the new prospect will be automatically assigned to the oldest existing campaign.

<a name="14833-updating-field-values" id="updating-field-values"></a>

## [](#updating-field-values-)Updating Field Values

Modifying values of prospect data fields is done by submitting an `update` request with parameters for each field to be updated. Each parameter is formatted as `<field_name>=<value>`. Custom field values are updated using the same syntax.

_**Example:** Updating the phone number of a prospect whose email address is_ `bob@pardot.com`: /api/prospect/version/3/do/update/email/[bob@pardot.com](mailto:bob@pardot.com)?phone=888-123-4567&amp;api_key=&amp;user_key=

Only values that are specifically named in the request are updated. All others are left unchanged. To clear a value, submit an `update` request containing a parameter with no specified value, such as `phone=`.

**_Note:_** Any field that is set to record multiple responses cannot have its values cleared this way.

<a name="14833-updating-fields-with-predefined-values" id="updating-fields-with-predefined-values"></a>

## [](#updating-fields-with-predefined-values-)Updating Fields with Predefined Values

Modifying values of prospect data fields with predefined values is accomplished through an `update` request with parameters for each field to be updated. Each parameter is formatted as `<field_name>=<value>` where `<value>` matches the predefined field value. Custom field values are updated using the same syntax.

_**Example:** Updating the category of a prospect whose email address is_ `bob@pardot.com` *to the category `consumer`: /api/prospect/version/3/do/update/email/[bob@pardot.com](mailto:bob@pardot.com)?category=consumer&amp;api_key=&amp;user_key=

<a name="14833-updating-fields-with-multiple-values" id="updating-fields-with-multiple-values"></a>

## [](#updating-fields-with-multiple-values-)Updating Fields with Multiple Values

Updating field values with multiple values follows the same convention as fields with predefined values, but requires a different parameter naming scheme to allow multiplicity. An `update` request is submitted with parameters formatted as `<field_name>_<count>=<field_value>` where `<count>` is an integer denoting the current parameter's place in sequence. `<count>` must start at 0 and increase by 1 until all desired values are submitted.

_**Example:** Modifying the values of a custom field with field name_ `past_jobs` _for a prospect with a Pardot ID of_ `5`: /api/prospect/version/3/do/update/id/5?past_jobs_0=janitor&amp;past_jobs_1=security&amp;api_key=&amp;user_key=

**Note:** Checkbox and multi-select fields are the only field types that can be updated in this manner. To clear all of the values for a checkbox or multi-select field, use `<field_name>_0=`. To clear specific values, just set the values that should remain in the prospect record using the method above.

<a name="14833-updating-email-list-subscriptions" id="updating-email-list-subscriptions"></a>

## [](#updating-email-list-subscriptions-)Updating Email List Subscriptions

To modify email list subscriptions for a prospect, the Pardot ID of the email list is required. Once the ID is obtained, an `update` is submitted with parameters formatted as `list_<list_id>=1` to create a subscription and `list_<list_id>=0` to end a subscription.

_**Example:** Adding a prospect whose email address is_ `bob@pardot.com` _to an email list with Pardot ID_ `8`: /api/prospect/version/3/do/update/email/[bob@pardot.com](mailto:bob@pardot.com)?list_8=1&amp;api_key=&amp;user_key=

Requests that attempt to subscribe a prospect to lists that it is already subscribed to are ignored. Unsubscribe requests are handled similarly.

<a name="14833-updating-profile-criteria-matching-statuses" id="updating-profile-criteria-matching-statuses"></a>

## [](#updating-profile-criteria-matching-statuses-)Updating Profile Criteria Matching Statuses

To modify a prospect's matching status for associated profile criteria, the Pardot ID of the profile criteria is required. Once the ID is obtained, an `update` is submitted with parameters formatted as `profile_criteria_<profile_criteria_id>=<status>`. The value of `<status>` may be either `match`, `nomatch`, or `unknown`.

_**Example:** Setting a profile criteria for a prospect whose email address is_ `bob@pardot.com` _to_ `match`: /api/prospect/version/3/do/update/email/[bob@pardot.com](mailto:bob@pardot.com)?profile_criteria_8=match&amp;api_key=&amp;user_key=_**Example:** Setting a profile criteria for a prospect with Pardot ID_ `58` _to_ `nomatch`: /api/prospect/version/3/do/update/id/58?profile_criteria_8=nomatch&amp;api_key=&amp;user_key=

Only profile criteria that belong to the profile associated with the prospect can be updated using this method. Requests to update profile criteria not associated with the assigned profile will be ignored. Using any matching status values other than `match`, `nomatch`, or `unknown` will result in an error message. See [Error Codes &amp; Messages](../error-codes-and-messages) for details.

<a name="14833-updating-prospect-account-matching-statuses" id="updating-prospect-account-matching-statuses"></a>

## [](#updating-prospect-account-associations-)Updating Prospect Account Associations

To modify a prospect's matching status for associated prospect account, the Pardot ID of the prospect account is required. Once the ID is obtained, an `update` is submitted with parameters formatted as `prospect_account_id=<id>`.

_**Example:** Setting a prospect account for a prospect whose email address is_ `bob@pardot.com` _to_ `match`: /api/prospect/version/3/do/update/email/[bob@pardot.com](mailto:bob@pardot.com)?prospect_account_id=&amp;api_key=&amp;user_key=

A prospect account with the id must exist, and can not be set if a CRM connector is set up in the account.
