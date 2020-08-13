# Send a notification to a user when their profile is updated

### <span style="text-decoration:underline;">Overview</span>
Users profiles can be updated for numerous reasons, it might be an automated changed, a scheduled change by the HR team, or even a personal change done by the user themselves. However can you always be sure that the data that has been changed is now correct or done so legitamely by the user?

This flow allows you to send a notification to the user (e.g. in a slack message or via an email notifcation) to let them know that their profile has been updated, so they can review the changes and contact somebody if it looks incorrect.

### <span style="text-decoration:underline;">Before you get Started / Prerequisites</span>
Before you get started, you will need:

*   Access to an Okta tenant with Okta Workflows enabled for your org 
*   Active users
*   A way to notify the user of profile changes (A connection to e.g: Slack, Office 365 mail, Gmail)


### <span style="text-decoration:underline;">Setup Steps</span>



1. Open the flow "Send notification to user when profile is updated"
2. Look at the "List - Construct" card, update this with the attributes you would like to monitor and notify the user if they have changed
3. In the "Branching - If/Else" card, there is two "Text - Compose" cards. You will want to update the contents of the message that it sent to the user based on the user updating their profile and if something else updated the users profile
4. Near the end of the flow, there is a "Text - Compose" card, update the message that you would like to send your user
5. At the end of the flow is a "Slack - Send Message to Channel" card, you will want to replace this, either to a direct message in Slack to the user, or using another service, such as sending the user an email with Office 365 or Gmail
4. Turn the flow ON.


### <span style="text-decoration:underline;">Testing this Flow</span>



1. Go to the flow and make sure flow history is enabled
2. Click "Test"
3. Minimum details that need to be entered: "Changed attributes", "Actor" & "Okta User". 
    i. Actor & Okta User need to be a JSON Object with "ID" & "Alternate ID" to be used to send notifcation - an example:
        {
            "ID": "an id",
            "Alternate ID": "user@domain.com"
        }
3. Click the Flow History and make sure everything succeeded.


### <span style="text-decoration:underline;">Limitations & Known Issues</span>


*   You have to have a connection to be able to notify the user
*   This example will notify the user if either they or somebody else changes their profile (it could be possible to make this a switchable feature)
*   If the user updates their own profile in a third party application (outside of Okta) that is updating their profile in Okta via API's, if this is using the SWSS API key, it will show as being somebody else. If the third party application uses oAuth for Okta API's, then it should show that the user updated their profile
