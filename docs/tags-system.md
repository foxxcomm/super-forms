# Tags system


* [What are {tags}?](#what-are-tags)
* [How to use tags?](#how-to-use-tags)
* [Setting and retrieving multiple values per option](#setting-and-retrieving-multiple-values-per-option)
* [When and where can I use tags?](#when-and-where-can-i-use-tags)
* [Predefined {tags} that are usefull](#predefined-tags-that-are-usefull)

### What are {tags}?

The tags system in **Super Forms** is a very simple but yet very powerfull feature that gives any form the **flexibility** you require.

A so called `{tag}` can retrieve the form data entered by a user **on the fly** for either later use in your emails, or to directly display it somewhere in your form to be displayed to the user itself.

A simple usecase would be to **summarize** the information entered by the user.


### How to use tags?

A tag is written with the so called curly braces `{}` with in between the curly braces the [unique field name](unique-field-name) of the element you wish to retrieve the value from.

When you have a field name called `first_name` and you want to retrieve this value in your email body you can retrieve it by placing `{first_name}` in the body.

**Example:**

    Dear {first_name} {last_name},
    ...

**Above will translate to:**

    Dear John Doe,
    ...


With checkboxes, radio buttons and dropdowns this will work exactly the same way except that you will also have the ability to retrieve the **label** instead of the **value**.

Let's say you added a checkbox element with the following options:
- My fav color is red | Red
- My fav color is green | Green
- My fav color is orange | Orange

The left side is your option `label` and on the right your `value`. 

If you would call your checkbox `fav_color` then you would retrieve the selected option values with the tag `{fav_color}`. But if you want to retrieve the label you can use `{fav_color;label}`.

**Example:**

    Selected color(s): {fav_color}
    Selected color(s): {fav_color;label}

    ...

**Above will translate to:**

    Selected color(s): Orange
    Selected color(s): My fav color is orange
    ...


### Setting and retrieving multiple values per options

Another feature you have with checkboxes, radio buttons and dropdowns is to **save multiple values** per value.

In order to do this the only thing you will have to do is **seperate each value** per option with a semicolon `;`.

For instance, when you sell multiple packages based on a specific membership, you might need a different price per membership.

Let's say we have a **Standard membership** and a **Gold membership**

We will ask the user to select a package.

We will use a checkbox field so the user can select wether or not they want this package.

The checkbox will be named `package_1` and has only 1 option named `Daily backups of your website` with the value `10;25`

Now whenever the user has selected the checkbox, we can retrieve the correct price depending on their membership.

To retrieve the Standard membership costs we would use the tag `{package_1;1}`

To retrieve the Gold membership costs we would use the tag `{package_1;2}`

Now you might ask where should I actually place this tag?

We can use the [Variable field](variable-field) to first determine what membership the user is, and then we return the correct price by entering the corresponding tag based on the variable field conditional logic.

?> **Please note:** If you use the [Calculator Add-on](calculator-add-on) and want to use it inside your math you must return an int value like so: `{package_1;1;int}` or `{package_1;2;int}`



### When and where can I use tags?

- Inside your E-mail bodies, Subjects, and all other email headers you could think of.
- In combination with [E-mail if statements](email-if-statements)
- Within your [HTML elements](html)
- Inside the Success Message that is displayed to the user after a successfull submitted form
- In combination with [Variable fields](variable-fields) and also within the conditional logic statements
- When redirecting form to a custom URL to add dynamic parameters e.g: domain.com/?first-name={first_name}&last-name={last_name}
- In validation option for text fields to conditionally check for same value as other field (to compare two field values)
- You can use tags when saving contact entries with a custom title



### Predefined {tags} that are usefull

**Tag to retrieve Cart information (when WooCommerce is installed and activated):**
- `{wc_cart_total}`, `{wc_cart_total_float}`, `{wc_cart_items}`, `{wc_cart_items_price}`

**Tag to retrieve the total submission count (if form locker is used):**
- `{submission_count}`

**Tag to retrieve the latest Contact Entry status that was created for this form:**
- `{last_entry_status}`

**Tag to save previous location (URL) in a session so it will not be subject to change after navigating away and returning back at later time:**
- `{server_http_referrer_session}` (saves HTTP_REFERRER (previous page URL) into session)

**Tag to retrieve the previous location (URL) where the user navigated from before landing on the page with the form:**
- `{server_http_referrer}` (saves HTTP_REFERRER (previous page URL) into session)

**Tags to retrieve current date values in server timestamp (UTC/GMT):**
- `{server_timestamp_gmt}`, `{server_day_gmt}`, `{server_month_gmt}`, `{server_year_gmt}`, `{server_hour_gmt}`, `{server_minute_gmt}`, `{server_seconds_gmt}` 

**Tags to retrieve current date values in server timestamp (Local time):**
- `{server_timestamp}`, `{server_day}`, `{server_month}`, `{server_year}`, `{server_hour}`, `{server_minute}`, `{server_seconds}`

**Tag to retrieve current post URL (permalink):**
- `{post_permalink}` (will retrieve the current post permalink where the form is placed on)

**Tag to retrieve contact entry ID that was created after submitting form:**
- `{contact_entry_id}` (can only be used in **Success Message** and E-mails)

**Tags to retrieve author information based on the current page/post the form is placed on:**
- `{post_author_id}` and `{post_author_email}` (can be used in both the [Hidden field](hidden-field) and [Text field](text-field) **Default value** option)

**Tags to retrieve values of logged in user:**
- `{user_login}`, `{user_email}`, `{user_firstname}`, `{user_lastname}`, `{user_display}`, `{user_id}`, `{user_roles}` (can be used in both the [Hidden field](hidden-field) and [Text field](text-field) **Default value** option)