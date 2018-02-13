.. _notifications-example-ug:

=======================
Notifications (example)
=======================

Rackspace Intelligence lets you create different types of notifications for
your entities. For example, you can define a method of contacting a support
engineer by SMS and a method of contacting a manager by email. You can also
create notification plans that work with your monitoring checks and alarms.
So, you can specify several ways to notify members of your team and then
assemble those notifications into notification plans.

.. contents::
   :depth: 2
   :local:
   :backlinks: none

Working with notifications
~~~~~~~~~~~~~~~~~~~~~~~~~~

You can create the following types of notifications:

- Webhook
- Email
- `PagerDuty <https://www.pagerduty.com/>`_
- SMS
- `VictorOps <https://victorops.com/>`_

To create new notifications or edit your existing notifications, click
**Notify** at the top of the Rackspace Intelligence interface, and then click
**Notifications**.

You can sort the list of notifications by name or type. For example, sorting by
type groups everyone who prefers to be notified by email.

For each notification, the **Detail** field contains specific contact
information such as an email ID or a telephone number.

Create a notification
---------------------

1. To define a new notification method, click **Create Notification**.
2. Enter a name for the notification, and choose a notification type.
3. Depending on the type that you chose, provide notification details,
   such as an email address or a phone number.
4. Click **Save Notification**.

The notification appears on the Notifications page.

Update the settings for a notification
--------------------------------------

To edit a notification, click the settings icon to the left of the
notification name on the Notifications page.

1. On the Notifications page, click the settings icon to the left of the
   notification, and select **Edit Notification**.
2. In the popup dialog box, make the necessary updates for the
     notification, and then click **Save Notification**.

Delete a notification
---------------------

1. On the Notifications page, click the settings icon to the left of the
   notification, and select **Delete**.
2. Click **Delete** to confirm the deletion of your notification.

   The notification is permanently deleted.

Working with notification plans
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To create a new notification plan or edit an existing notification plan,
click **Notify** at the top of the Rackspace Intelligence interface and then
click **Notification Plans**.

You can sort the list of notification plans by name, number of
notifications, or number of alarms. Sorting by the number of alarms can help
you prioritize follow-up investigations.

Create a notification plan
--------------------------

To create a usable notification plan, create the plan itself and then add at
least one notification to the plan. You can add existing notifications or
create new ones.

1. On the Notification Plans page, click **Create Notification Plan**.

2. In the dialog box, type a name for the notification plan and
   click **Create Notification Plan**.

3. On the Notifications page for the plan, click **Add Notifications**.

4. To add an existing notification, click the **Select** button next to
   the notification, and then select at least one level for which the
   notification will be activated: **Critical**, **Warning**, or **OK**.

3. To create a notification and add it to the plan, perform the following
   steps:

    1. Click **Create a new notification**.
    2. Enter a name for the notification and choose a notification type.
    3. Depending on the type that you chose, provide notification details, such
       as an email address or a phone number.
    4. Click **Create and Select Notification**.
    5. Select at least one level for which the notification will be
       activated: **Critical**, **Warning**, or **OK**.

4. Click **Save Notification Plan**.

Your notification plan is saved and displayed on the Notification
Plans overview page.

Rename a notification plan
--------------------------

1. On the details page for the notification plan, click the **Actions** menu
   and select **Rename Plan**.

2. In the **Rename Notification Plan** box, type the new name, and then
   click **Rename**.

Change the notifications in a notification plan
-----------------------------------------------

1. On the details page for the notification plan, click the **Actions** menu
   and select **Add Notifications**.

2. In the dialog box, select one or more notifications to add, or
   click **Create a new notification** to create a new notification
   plan. Both options are described in the "Create a notification plan"
   section.

3. If you want to remove a notification, click **Deselect** beside it.

4. Click **Save Notification Plan**.

Delete a notification plan
--------------------------

1. On the details page for the notification plan, click the **Actions** menu
   and select **Delete Plan**.

2. Click **Delete** to permanently delete the plan.

   Rackspace Intelligence permanently deletes the notification plan
   from the database.
