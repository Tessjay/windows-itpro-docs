---
title: Limitations while using Windows Information Protection (WIP) (Windows 10)
description: This section includes info about the common problems you might encounter while using Windows Information Protection (WIP).
keywords: WIP, Windows Information Protection, EDP, Enterprise Data Protection
ms.prod: w10
ms.mktglfcycl: explore
ms.sitesec: library
ms.pagetype: security
author: eross-msft
localizationpriority: high
---

# Limitations while using Windows Information Protection (WIP)
**Applies to:**

-   Windows 10, version 1607
-   Windows 10 Mobile

This table provides info about the most common problems you might encounter while running WIP in your organization.

<table>
    <tr>
        <th>Limitation</th>
        <th>How it appears</th>
        <th>Workaround</th>
    </tr>
    <tr>
        <td>Your enterprise data on USB drives might be tied to the device it was protected on, based on your Azure RMS configuration.</td>
        <td><strong>If you’re using Azure RMS:</strong> Authenticated users can open enterprise data on USB drives, on computers running the latest build from the Windows Insider Program.<p><strong>If you’re not using Azure RMS:</strong> Data in the new location remains encrypted, but becomes inaccessible on other devices and for other users. For example, the file won't open or the file opens, but doesn't contain readable text.</td>
        <td>Share files with fellow employees through enterprise file servers or enterprise cloud locations. If data must be shared via USB, employees can decrypt protected files, but it will be audited.<p>We strongly recommend educating employees about how to limit or eliminate the need for this decryption.</td>
    </tr>
    <tr>
        <td>Direct Access is incompatible with WIP.</td>
        <td>Direct Access might experience problems with how WIP enforces app behavior and data movement because of how WIP determines what is and isn’t a corporate network resource.</td>
        <td>We recommend that you use VPN for client access to your intranet resources.<p><strong>Note</strong><br>VPN is optional and isn’t required by WIP.</td>
    </tr>
    <tr>
        <td><strong>NetworkIsolation</strong> Group Policy setting is incompatible with WIP.</td>
        <td>The <strong>NetworkIsolation</strong> Group Policy setting has incompatible network settings that can conflict and cause problems with WIP.</td>
        <td>We recommend that you don’t use the NetworkIsolation Group Policy setting.</td>
    </tr>
    <tr>
        <td>Cortana can potentially allow data leakage if it’s on the allowed apps list.</td>
        <td>If Cortana is on the allowed list, some files might become unexpectedly encrypted after an employee performs a search using Cortana. Your employees will still be able to use Cortana to search and provide results on enterprise documents and locations, but results might be sent to Microsoft.</td>
        <td>We don’t recommend adding Cortana to your allowed apps list. However, if you wish to use Cortana and don't mind whether the results potentially go to Microsoft, you can make Cortana an Exempt app.</td>
    </tr>
    <tr>
        <td>WIP is designed for use by a single user per device.</td>
        <td>A secondary user on a device might experience app compat issues when unenlightened apps start to automatically encrypt for all users. Additionally, only the initial, enrolled user’s content can be revoked during the unenrollment process.</td>
        <td>We recommend only having one user per managed device.</td>
    </tr>
    <tr>
        <td>Installers copied from an enterprise network file share might not work properly.</td>
        <td>An app might fail to properly install because it can’t read a necessary configuration or data file, such as a .cab or .xml file needed for installation, which was protected by the copy action.</td>
        <td>To fix this, you can:
            <ul>
                <li>Start the installer directly from the file share.<p>-OR-</li>
                <li>Decrypt the locally copied files needed by the installer.<p>-OR-</li>
                <li>Mark the file share with the installation media as “personal”. To do this, you’ll need to set the Enterprise IP ranges as <strong>Authoritative</strong> and then exclude the IP address of the file server, or you’ll need to put the file server on the Enterprise Proxy Server list.</li>
            </ul></td>
    </tr>
    <tr>
        <td>Changing your primary Corporate Identity isn’t supported.</td>
        <td>You might experience various instabilities, including but not limited to network and file access failures, and potentially granting incorrect access.</td>
        <td>Turn off WIP for all devices before changing the primary Corporate Identity (first entry in the list), restarting, and finally redeploying.</td>
    </tr>
    <tr>
        <td>Redirected folders with Client Side Caching are not compatible with WIP.</td>
        <td>Apps might encounter access errors while attempting to read a cached, offline file.</td>
        <td>Migrate to use another file synchronization method, such as Work Folders or OneDrive for Business.<p><strong>Note</strong><br>For more info about Work Folders and Offline Files, see the blog, [Work Folders and Offline Files support for Windows Information Protection](https://blogs.technet.microsoft.com/filecab/2016/08/29/work-folders-and-offline-files-support-for-windows-information-protection/). If you're having trouble opening files offline while using Offline Files and WIP, see the support article, [Can't open files offline when you use Offline Files and Windows Information Protection](https://support.microsoft.com/en-us/kb/3187045).</td>
    </tr>
    <tr>
        <td>You can't upload an enterprise file to a personal location using Microsoft Edge or Internet Explorer.</td>
        <td>A message appears stating that the content is marked as <strong>Work</strong> and the user isn't given an option to override to <strong>Personal</strong>.</td>
        <td>Open File Explorer and change the file ownership to <strong>Personal</strong> before you upload.</td>
    </tr>
    <tr>
        <td>ActiveX controls should be used with caution.</td>
        <td>Webpages that use ActiveX controls can potentially communicate with other outside processes that aren’t protected by using WIP.</td>
        <td>We recommend that you switch to using Microsoft Edge, the more secure and safer browser that prevents the use of ActiveX controls. We also recommend that you limit the usage of Internet Explorer 11 to only those line-of-business apps that require legacy technology.<p>For more info, see [Out-of-date ActiveX control blocking](https://technet.microsoft.com/en-us/itpro/internet-explorer/ie11-deploy-guide/out-of-date-activex-control-blocking).</td>
    </tr>
</table>

>[!NOTE]
>Help to make this topic better by providing us with edits, additions, and feedback. For info about how to contribute to this topic, see [Contributing to TechNet content](https://github.com/Microsoft/windows-itpro-docs/blob/master/CONTRIBUTING.md).       
