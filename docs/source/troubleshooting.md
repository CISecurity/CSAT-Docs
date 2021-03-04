![](img/CIS_CSAT_Pro_RGB.png)


# CIS CSAT Pro Troubleshooting#
----------
<a name="introduction"></a>
##Implementation Group dropdown issue ##

Prior to the CSAT Pro v1.5.0 release, the Implementation Group (IG) dropdown action (available from the Assessment Dashboard) had a bug causing it to affect the applicability of Sub-Controls in all assessments, rather than just the current assessment as intended.  
Please note: due to this bug, the Implementation Group dropdown on an Assessment's Dashboard may not accurately reflect the assessment's current IG settings. For instance, consider the case:
 
1. The Assessment A dropdown was set to "IG-1"
1. Later the Assessment B dropdown was set to "IG-1 & IG-2"

This would erroneously result in the dropdown on the Assessment A Dashboard still displaying "IG-1", but the IG2 Sub-Controls in Assessment A would actually be applicable.

If you have used the Implementation Group dropdown, we recommend that you review the Sub-Control applicability settings for your assessments to ensure that they are set as intended.  This can be done by going to the Assessment Summary page where you can see a listing of all of the assessment's Sub-Controls and their applicability; the Assessment Summary page will also let you filter by categories such as "Applicable" and "Implementation Group".

Here is some specific guidance for different cases:

1. If you have not used the Implementation Group dropdown on any assessment's Dashboard, you should not be affected by this bug.
1. If all the assessments in your CSAT Pro instance use the same IG and you don't use any custom applicability flags for individual Sub-Controls, then this bug shouldn't affect you.
1. If you use different IGs for different assessments in your CSAT Pro instance, but you do not use custom applicability flags for individual Sub-Controls, then you might be affected by this bug.  You should review your assessment's Sub-Control applicability on the Assessment Summary page as described above.  Because you are using the IGs without any deviations (no custom Sub-Control applicability changes), you should be able to use the fixed Implementation Group dropdown (in v1.5.0 or after) for each assessment whose Sub-Control applicability does not match the intended IG.  You might have to switch to a different IG and then back to the desired IG.
1. If you use the IG dropdown and also use custom Sub-Control applicability flags, then you might be affected by this bug.  You should review your assessment's Sub-Control applicability on the Assessment Summary page as described above.  Any custom Sub-Control applicability settings that are not correct will need to be manually reapplied.

Please note: we hope to provide a Bulk Applicability update feature in v1.6.0 of CSAT Pro.  Once that feature is available, it should make the process of making applicability changes from the Assessment Summary page easier.




