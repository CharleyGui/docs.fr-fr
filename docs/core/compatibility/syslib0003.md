---
title: AVERTISSEMENT SYSLIB0003
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0003.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: ca774f3e4b5132cf40c632f7c49d3f183f5d578f
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333291"
---
# <a name="syslib0003-code-access-security-is-not-supported"></a><span data-ttu-id="23346-103">SYSLIB0003 : la sécurité d’accès du code n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="23346-103">SYSLIB0003: Code access security is not supported</span></span>

<span data-ttu-id="23346-104">La [sécurité d’accès du code (cas)](../../framework/data/adonet/code-access-security.md) est une technologie héritée non prise en charge.</span><span class="sxs-lookup"><span data-stu-id="23346-104">[Code access security (CAS)](../../framework/data/adonet/code-access-security.md) is an unsupported, legacy technology.</span></span> <span data-ttu-id="23346-105">L’infrastructure permettant d’activer les autorités de certification, qui existe uniquement dans .NET Framework 2. x-4. x, est dépréciée et ne reçoit pas de correctifs de sécurité ou de maintenance.</span><span class="sxs-lookup"><span data-stu-id="23346-105">The infrastructure to enable CAS, which exists only in .NET Framework 2.x - 4.x, is deprecated and not receiving servicing or security fixes.</span></span>

<span data-ttu-id="23346-106">En conséquence, la plupart des types liés à la sécurité d’accès du code (CAS) dans .NET sont obsolètes, à partir de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="23346-106">As a result, most code access security (CAS)-related types in .NET are obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="23346-107">Cela comprend les attributs CAS, tels que <xref:System.Security.Permissions.SecurityPermissionAttribute> , les objets d’autorisation cas, tels que les <xref:System.Net.SocketPermission> <xref:System.Security.Policy.EvidenceBase> types dérivés de, et d’autres API de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="23346-107">This includes CAS attributes, such as <xref:System.Security.Permissions.SecurityPermissionAttribute>, CAS permission objects, such as <xref:System.Net.SocketPermission>, <xref:System.Security.Policy.EvidenceBase>-derived types, and other supporting APIs.</span></span> <span data-ttu-id="23346-108">L’utilisation de ces API génère un avertissement `SYSLIB0003` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="23346-108">Using these APIs generates warning `SYSLIB0003` at compile time.</span></span>

<span data-ttu-id="23346-109">La liste complète des API obsolètes de l’autorité de certification est la suivante :</span><span class="sxs-lookup"><span data-stu-id="23346-109">The complete list of obsolete CAS APIs is as follows:</span></span>

- <xref:System.AppDomain.PermissionSet?displayProperty=fullName>
- <xref:System.Configuration.ConfigurationPermission?displayProperty=fullName>
- <xref:System.Configuration.ConfigurationPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.Common.DBDataPermission?displayProperty=fullName>
- <xref:System.Data.Common.DBDataPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.Odbc.OdbcPermission?displayProperty=fullName>
- <xref:System.Data.Odbc.OdbcPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.OleDb.OleDbPermission?displayProperty=fullName>
- <xref:System.Data.OleDb.OleDbPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.OracleClient.OraclePermission?displayProperty=fullName>
- <xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=fullName>
- <xref:System.Data.SqlClient.SqlClientPermission?displayProperty=fullName>
- <xref:System.Data.SqlClient.SqlClientPermissionAttribute?displayProperty=fullName>
- <xref:System.Diagnostics.EventLogPermission?displayProperty=fullName>
- <xref:System.Diagnostics.EventLogPermissionAttribute?displayProperty=fullName>
- <xref:System.Diagnostics.PerformanceCounterPermission?displayProperty=fullName>
- <xref:System.Diagnostics.PerformanceCounterPermissionAttribute?displayProperty=fullName>
- <xref:System.DirectoryServices.DirectoryServicesPermission?displayProperty=fullName>
- <xref:System.DirectoryServices.DirectoryServicesPermissionAttribute?displayProperty=fullName>
- <xref:System.Drawing.Printing.PrintingPermission?displayProperty=fullName>
- <xref:System.Drawing.Printing.PrintingPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.DnsPermission?displayProperty=fullName>
- <xref:System.Net.DnsPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.Mail.SmtpPermission?displayProperty=fullName>
- <xref:System.Net.Mail.SmtpPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.NetworkInformation.NetworkInformationPermission?displayProperty=fullName>
- <xref:System.Net.NetworkInformation.NetworkInformationPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermission?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.PnrpPermission?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.PnrpPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.SocketPermission?displayProperty=fullName>
- <xref:System.Net.SocketPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.WebPermission?displayProperty=fullName>
- <xref:System.Net.WebPermissionAttribute?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.AllowReversePInvokeCallsAttribute?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission?displayProperty=fullName>
- <xref:System.Security.HostProtectionException?displayProperty=fullName>
- <xref:System.Security.IPermission?displayProperty=fullName>
- <xref:System.Security.IStackWalk?displayProperty=fullName>
- <xref:System.Security.NamedPermissionSet?displayProperty=fullName>
- <xref:System.Security.PermissionSet?displayProperty=fullName>
- <xref:System.Security.Permissions.CodeAccessSecurityAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.GacIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.GacIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.HostProtectionResource?displayProperty=fullName>
- <xref:System.Security.Permissions.IUnrestrictedPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageContainment?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageFilePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageFilePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStoragePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStoragePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntry?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntryCollection?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntryEnumerator?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionAudio?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionImage?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionVideo?displayProperty=fullName>
- <xref:System.Security.Permissions.PermissionSetAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PermissionState?displayProperty=fullName>
- <xref:System.Security.Permissions.PrincipalPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PublisherIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.PublisherIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ResourcePermissionBase?displayProperty=fullName>
- <xref:System.Security.Permissions.ResourcePermissionBaseEntry?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermissionFlag?displayProperty=fullName>
- <xref:System.Security.Permissions.SiteIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.SiteIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNameIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNamePublicKeyBlob?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionClipboard?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionWindow?displayProperty=fullName>
- <xref:System.Security.Permissions.UrlIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.UrlIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermissionLevel?displayProperty=fullName>
- <xref:System.Security.Permissions.ZoneIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.ZoneIdentityPermissionAttribute?displayProperty=fullName>
- [<span data-ttu-id="23346-110">System. Security. Policy. ApplicationTrust. ApplicationTrust (PermissionSet, IEnumerable \<StrongName> )</span><span class="sxs-lookup"><span data-stu-id="23346-110">System.Security.Policy.ApplicationTrust.ApplicationTrust(PermissionSet, IEnumerable\<StrongName>)</span></span>](/dotnet/api/system.security.policy.applicationtrust.-ctor#System_Security_Policy_ApplicationTrust__ctor_System_Security_PermissionSet_System_Collections_Generic_IEnumerable_System_Security_Policy_StrongName__)
- <xref:System.Security.Policy.ApplicationTrust.FullTrustAssemblies?displayProperty=fullName>
- <xref:System.Security.Policy.FileCodeGroup?displayProperty=fullName>
- <xref:System.Security.Policy.GacInstalled?displayProperty=fullName>
- <xref:System.Security.Policy.IIdentityPermissionFactory?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.AddNamedPermissionSet(System.Security.NamedPermissionSet)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.ChangeNamedPermissionSet(System.String,System.Security.PermissionSet)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.GetNamedPermissionSet(System.String)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.RemoveNamedPermissionSet%2A?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyStatement.PermissionSet?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyStatement.%23ctor%2A?displayProperty=fullName>
- <xref:System.Security.Policy.Publisher?displayProperty=fullName>
- <xref:System.Security.Policy.Site?displayProperty=fullName>
- <xref:System.Security.Policy.StrongName?displayProperty=fullName>
- <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=fullName>
- <xref:System.Security.Policy.Url?displayProperty=fullName>
- <xref:System.Security.Policy.Zone?displayProperty=fullName>
- <xref:System.Security.SecurityManager?displayProperty=fullName>
- <xref:System.ServiceProcess.ServiceControllerPermission?displayProperty=fullName>
- <xref:System.ServiceProcess.ServiceControllerPermissionAttribute?displayProperty=fullName>
- <xref:System.Transactions.DistributedTransactionPermission?displayProperty=fullName>
- <xref:System.Transactions.DistributedTransactionPermissionAttribute?displayProperty=fullName>
- <xref:System.Web.AspNetHostingPermission?displayProperty=fullName>
- <xref:System.Web.AspNetHostingPermissionAttribute?displayProperty=fullName>
- <xref:System.Xaml.Permissions.XamlLoadPermission?displayProperty=fullName>

## <a name="workarounds"></a><span data-ttu-id="23346-111">Solutions de contournement</span><span class="sxs-lookup"><span data-stu-id="23346-111">Workarounds</span></span>

- <span data-ttu-id="23346-112">Si vous déclarez une autorisation de sécurité, supprimez l’attribut ou l’appel qui déclare l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="23346-112">If you're asserting any security permission, remove the attribute or call that asserts the permission.</span></span>

  ```csharp
  // REMOVE the attribute below.
  [SecurityPermission(SecurityAction.Assert, ControlThread = true)]
  public void DoSomething()
  {
  }
  public void DoAssert()
  {
      // REMOVE the line below.
      new SecurityPermission(SecurityPermissionFlag.ControlThread).Assert();
  }
  ```

- <span data-ttu-id="23346-113">Si vous refusez ou restreignez (via `PermitOnly` ) toute autorisation, contactez votre conseiller de sécurité.</span><span class="sxs-lookup"><span data-stu-id="23346-113">If you're denying or restricting (via `PermitOnly`) any permission, contact your security advisor.</span></span> <span data-ttu-id="23346-114">Étant donné que les attributs CAS ne sont pas honorés par le Runtime .NET 5.0 +, votre application peut avoir une brèche de sécurité si elle s’appuie incorrectement sur l’infrastructure CAS pour restreindre l’accès à ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="23346-114">Because CAS attributes are not honored by the .NET 5.0+ runtime, your application could have a security hole if it incorrectly relies on the CAS infrastructure to restrict access to these methods.</span></span>

  ```csharp
  // REVIEW the attribute below; could indicate security vulnerability.
  [SecurityPermission(SecurityAction.Deny, ControlThread = true)]
  public void DoSomething()
  {
  }
  public void DoPermitOnly()
  {
      // REVIEW the line below; could indicate security vulnerability.
      new SecurityPermission(SecurityPermissionFlag.ControlThread).PermitOnly();
  }
  ```

- <span data-ttu-id="23346-115">Si vous exigez une autorisation (sauf <xref:System.Security.Permissions.PrincipalPermission> ), supprimez la demande.</span><span class="sxs-lookup"><span data-stu-id="23346-115">If you're demanding any permission (except <xref:System.Security.Permissions.PrincipalPermission>), remove the demand.</span></span> <span data-ttu-id="23346-116">Toutes les demandes échoueront au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="23346-116">All demands will succeed at run time.</span></span>

  ```csharp
  // REMOVE the attribute below; it will always succeed.
  [SecurityPermission(SecurityAction.Demand, ControlThread = true)]
  public void DoSomething()
  {
  }
  public void DoDemand()
  {
      // REMOVE the line below; it will always succeed.
      new SecurityPermission(SecurityPermissionFlag.ControlThread).Demand();
  }
  ```

- <span data-ttu-id="23346-117">Si vous en avez <xref:System.Security.Permissions.PrincipalPermission> l’exigence, consultez les conseils pour [SYSLIB0002 : PrincipalPermissionAttribute est obsolète](syslib0002.md#workarounds).</span><span class="sxs-lookup"><span data-stu-id="23346-117">If you're demanding <xref:System.Security.Permissions.PrincipalPermission>, consult the guidance for [SYSLIB0002: PrincipalPermissionAttribute is obsolete](syslib0002.md#workarounds).</span></span> <span data-ttu-id="23346-118">Ces instructions s’appliquent à la fois à <xref:System.Security.Permissions.PrincipalPermission> et <xref:System.Security.Permissions.PrincipalPermissionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="23346-118">That guidance applies for both <xref:System.Security.Permissions.PrincipalPermission> and <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>

## <a name="see-also"></a><span data-ttu-id="23346-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23346-119">See also</span></span>

- [<span data-ttu-id="23346-120">SYSLIB0002 : PrincipalPermissionAttribute est obsolète</span><span class="sxs-lookup"><span data-stu-id="23346-120">SYSLIB0002: PrincipalPermissionAttribute is obsolete</span></span>](syslib0002.md)
