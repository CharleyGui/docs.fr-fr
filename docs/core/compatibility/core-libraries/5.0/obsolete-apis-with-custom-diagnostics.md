---
title: 'Modification avec rupture : API obsoletions avec ID de diagnostics autres que ceux par défaut'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où certaines API ont été marquées comme obsolètes avec un ID de diagnostic personnalisé.
ms.date: 11/01/2020
ms.openlocfilehash: 9bd7ce18aed38955f9abc91e0c8b09e827c401d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761165"
---
# <a name="api-obsoletions-with-non-default-diagnostic-ids"></a><span data-ttu-id="35f79-103">Obsoletions d’API avec ID de diagnostics autres que ceux par défaut</span><span class="sxs-lookup"><span data-stu-id="35f79-103">API obsoletions with non-default diagnostic IDs</span></span>

<span data-ttu-id="35f79-104">Certaines API ont été marquées comme obsolètes, à partir de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="35f79-104">Some APIs have been marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="35f79-105">Cette modification avec rupture est spécifique aux API qui ont été marquées comme obsolètes *avec un ID de diagnostic personnalisé*.</span><span class="sxs-lookup"><span data-stu-id="35f79-105">This breaking change is specific to APIs that have been marked as obsolete *with a custom diagnostic ID*.</span></span> <span data-ttu-id="35f79-106">La suppression de l’ID de diagnostic obsoletion par défaut, qui est [CS0618](../../../../csharp/language-reference/compiler-messages/cs0618.md) pour le compilateur C#, ne supprime pas les avertissements générés par le compilateur lorsque ces API sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="35f79-106">Suppressing the default obsoletion diagnostic ID, which is [CS0618](../../../../csharp/language-reference/compiler-messages/cs0618.md) for the C# compiler, does not suppress the warnings that the compiler generates when these APIs are used.</span></span>

## <a name="change-description"></a><span data-ttu-id="35f79-107">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="35f79-107">Change description</span></span>

<span data-ttu-id="35f79-108">Dans les versions précédentes de .NET, ces API peuvent être utilisées sans aucun avertissement de génération.</span><span class="sxs-lookup"><span data-stu-id="35f79-108">In previous .NET versions, these APIs can be used without any build warning.</span></span> <span data-ttu-id="35f79-109">Dans .NET 5,0 et versions ultérieures, l’utilisation de ces API génère un avertissement ou une erreur au moment de la compilation avec un ID de diagnostic personnalisé.</span><span class="sxs-lookup"><span data-stu-id="35f79-109">In .NET 5.0 and later versions, use of these APIS produces a compile-time warning or error with a custom diagnostic ID.</span></span> <span data-ttu-id="35f79-110">L’utilisation d’ID de diagnostic personnalisés vous permet de supprimer les avertissements obsoletion individuellement au lieu de supprimer tous les avertissements obsoletion.</span><span class="sxs-lookup"><span data-stu-id="35f79-110">The use of custom diagnostic IDs allows you to suppress the obsoletion warnings individually instead of blanket-suppressing all obsoletion warnings.</span></span>

<span data-ttu-id="35f79-111">Le tableau suivant répertorie les ID de diagnostic personnalisés et leurs messages d’avertissement correspondants pour les API obsolètes.</span><span class="sxs-lookup"><span data-stu-id="35f79-111">The following table lists the custom diagnostic IDs and their corresponding warning messages for obsoleted APIs.</span></span>

| <span data-ttu-id="35f79-112">ID de diagnostic</span><span class="sxs-lookup"><span data-stu-id="35f79-112">Diagnostic ID</span></span> | <span data-ttu-id="35f79-113">Description</span><span class="sxs-lookup"><span data-stu-id="35f79-113">Description</span></span> | <span data-ttu-id="35f79-114">severity</span><span class="sxs-lookup"><span data-stu-id="35f79-114">Severity</span></span> |
| - | - |
| `SYSLIB0001` | <span data-ttu-id="35f79-115">L’encodage UTF-7 n’est pas sécurisé et ne doit pas être utilisé.</span><span class="sxs-lookup"><span data-stu-id="35f79-115">The UTF-7 encoding is insecure and should not be used.</span></span> <span data-ttu-id="35f79-116">Envisagez plutôt d’utiliser UTF-8.</span><span class="sxs-lookup"><span data-stu-id="35f79-116">Consider using UTF-8 instead.</span></span> | <span data-ttu-id="35f79-117">Avertissement</span><span class="sxs-lookup"><span data-stu-id="35f79-117">Warning</span></span> |
| `SYSLIB0002` | <span data-ttu-id="35f79-118"><xref:System.Security.Permissions.PrincipalPermissionAttribute> n’est pas respecté par le runtime et ne doit pas être utilisé.</span><span class="sxs-lookup"><span data-stu-id="35f79-118"><xref:System.Security.Permissions.PrincipalPermissionAttribute> is not honored by the runtime and must not be used.</span></span> | <span data-ttu-id="35f79-119">Erreur</span><span class="sxs-lookup"><span data-stu-id="35f79-119">Error</span></span> |
| `SYSLIB0003` | <span data-ttu-id="35f79-120">La sécurité d’accès du code (CAS) n’est pas prise en charge ou respectée par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="35f79-120">Code access security (CAS) is not supported or honored by the runtime.</span></span> | <span data-ttu-id="35f79-121">Avertissement</span><span class="sxs-lookup"><span data-stu-id="35f79-121">Warning</span></span> |
| `SYSLIB0004` | <span data-ttu-id="35f79-122">La fonctionnalité de région d’exécution limitée n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="35f79-122">The constrained execution region (CER) feature is not supported.</span></span> | <span data-ttu-id="35f79-123">Avertissement</span><span class="sxs-lookup"><span data-stu-id="35f79-123">Warning</span></span> |
| `SYSLIB0005` | <span data-ttu-id="35f79-124">Le Global Assembly Cache (GAC) n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="35f79-124">The global assembly cache (GAC) is not supported.</span></span> | <span data-ttu-id="35f79-125">Avertissement</span><span class="sxs-lookup"><span data-stu-id="35f79-125">Warning</span></span> |
| `SYSLIB0006` | <span data-ttu-id="35f79-126"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> n’est pas pris en charge et lève une exception <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="35f79-126"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="35f79-127">Avertissement</span><span class="sxs-lookup"><span data-stu-id="35f79-127">Warning</span></span> |
| `SYSLIB0007` | <span data-ttu-id="35f79-128">L’implémentation par défaut de cet algorithme de chiffrement n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="35f79-128">The default implementation of this cryptography algorithm is not supported.</span></span> | <span data-ttu-id="35f79-129">Avertissement</span><span class="sxs-lookup"><span data-stu-id="35f79-129">Warning</span></span> |
| `SYSLIB0008` | <span data-ttu-id="35f79-130">L' <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API n’est pas prise en charge et lève une exception <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="35f79-130">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="35f79-131">Avertissement</span><span class="sxs-lookup"><span data-stu-id="35f79-131">Warning</span></span> |
| `SYSLIB0009` | <span data-ttu-id="35f79-132">Les <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> méthodes et ne <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> sont pas prises en charge et lèvent <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="35f79-132">The <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> and <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> methods are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="35f79-133">Avertissement</span><span class="sxs-lookup"><span data-stu-id="35f79-133">Warning</span></span> |
| `SYSLIB0010`| <span data-ttu-id="35f79-134">Certaines API de communication à distance ne sont pas prises en charge et lèvent <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="35f79-134">Some remoting APIs are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="35f79-135">Avertissement</span><span class="sxs-lookup"><span data-stu-id="35f79-135">Warning</span></span> |
| `SYSLIB0011` | <span data-ttu-id="35f79-136"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> la sérialisation est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="35f79-136"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is obsolete and should not be used.</span></span> | <span data-ttu-id="35f79-137">Avertissement</span><span class="sxs-lookup"><span data-stu-id="35f79-137">Warning</span></span> |
| `SYSLIB0012` | <span data-ttu-id="35f79-138"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> et <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> sont uniquement inclus pour la compatibilité .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="35f79-138"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> and <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> are only included for .NET Framework compatibility.</span></span> <span data-ttu-id="35f79-139">Utilisez plutôt <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="35f79-139">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span> | <span data-ttu-id="35f79-140">Avertissement</span><span class="sxs-lookup"><span data-stu-id="35f79-140">Warning</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="35f79-141">Version introduite</span><span class="sxs-lookup"><span data-stu-id="35f79-141">Version introduced</span></span>

<span data-ttu-id="35f79-142">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="35f79-142">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="35f79-143">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="35f79-143">Recommended action</span></span>

- <span data-ttu-id="35f79-144">Suivez les instructions spécifiques fournies pour chaque ID de diagnostic à l’aide du lien URL fourni dans l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="35f79-144">Follow the specific guidance provided for the each diagnostic ID using the URL link provided on the warning.</span></span>

- <span data-ttu-id="35f79-145">Les avertissements ou les erreurs pour ces obsoletions ne peuvent pas être supprimés à l’aide de l’ID de diagnostic standard pour les types ou membres obsolètes. Utilisez la valeur d’ID de diagnostic personnalisé à la `SYSLIBxxxx` place.</span><span class="sxs-lookup"><span data-stu-id="35f79-145">Warnings or errors for these obsoletions can't be suppressed using the standard diagnostic ID for obsolete types or members; use the custom `SYSLIBxxxx` diagnostic ID value instead.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="35f79-146">API affectées</span><span class="sxs-lookup"><span data-stu-id="35f79-146">Affected APIs</span></span>

### <a name="syslib0001"></a><span data-ttu-id="35f79-147">SYSLIB0001</span><span class="sxs-lookup"><span data-stu-id="35f79-147">SYSLIB0001</span></span>

- <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>
- <xref:System.Text.UTF7Encoding.%23ctor%2A>

### <a name="syslib0002"></a><span data-ttu-id="35f79-148">SYSLIB0002</span><span class="sxs-lookup"><span data-stu-id="35f79-148">SYSLIB0002</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute.%23ctor(System.Security.Permissions.SecurityAction)>

### <a name="syslib0003"></a><span data-ttu-id="35f79-149">SYSLIB0003</span><span class="sxs-lookup"><span data-stu-id="35f79-149">SYSLIB0003</span></span>

<span data-ttu-id="35f79-150">Classes dans l' `System.Security.Permissions` espace de noms :</span><span class="sxs-lookup"><span data-stu-id="35f79-150">Classes in the `System.Security.Permissions` namespace:</span></span>

- <xref:System.Security.Permissions.CodeAccessSecurityAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.GacIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.GacIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageFilePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageFilePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStoragePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStoragePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntry?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntryCollection?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntryEnumerator?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PermissionSetAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PrincipalPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PublisherIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.PublisherIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ResourcePermissionBase?displayProperty=fullName>
- <xref:System.Security.Permissions.ResourcePermissionBaseEntry?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.SiteIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.SiteIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNameIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNamePublicKeyBlob?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.UrlIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.UrlIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ZoneIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.ZoneIdentityPermissionAttribute?displayProperty=fullName>

<span data-ttu-id="35f79-151">Les classes qui dérivent de `CodeAccessSecurityAttribute` :</span><span class="sxs-lookup"><span data-stu-id="35f79-151">Classes that derive from `CodeAccessSecurityAttribute`:</span></span>

- <xref:System.Configuration.ConfigurationPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.Common.DBDataPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.Odbc.OdbcPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.OleDb.OleDbPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=fullName>
- <xref:System.Data.SqlClient.SqlClientPermissionAttribute?displayProperty=fullName>
- <xref:System.Diagnostics.EventLogPermissionAttribute?displayProperty=fullName>
- <xref:System.Diagnostics.PerformanceCounterPermissionAttribute?displayProperty=fullName>
- <xref:System.DirectoryServices.DirectoryServicesPermissionAttribute?displayProperty=fullName>
- <xref:System.Drawing.Printing.PrintingPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.DnsPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.SocketPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.WebPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.Mail.SmtpPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.NetworkInformation.NetworkInformationPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.PnrpPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermissionAttribute?displayProperty=fullName>
- <xref:System.ServiceProcess.ServiceControllerPermissionAttribute?displayProperty=fullName>
- <xref:System.Transactions.DistributedTransactionPermissionAttribute?displayProperty=fullName>
- <xref:System.Web.AspNetHostingPermissionAttribute?displayProperty=fullName>

<span data-ttu-id="35f79-152">Interfaces :</span><span class="sxs-lookup"><span data-stu-id="35f79-152">Interfaces:</span></span>

- <xref:System.Security.Permissions.IUnrestrictedPermission?displayProperty=fullName>
- <xref:System.Security.IPermission?displayProperty=fullName>
- <xref:System.Security.IStackWalk?displayProperty=fullName>
- <xref:System.Security.Policy.IIdentityPermissionFactory?displayProperty=fullName>

<span data-ttu-id="35f79-153">Les classes qui implémentent `IStackWalk` :</span><span class="sxs-lookup"><span data-stu-id="35f79-153">Classes that implement `IStackWalk`:</span></span>

- <xref:System.Security.NamedPermissionSet?displayProperty=fullName>
- <xref:System.Security.PermissionSet?displayProperty=fullName>

<span data-ttu-id="35f79-154">Les classes qui implémentent `IPermission` :</span><span class="sxs-lookup"><span data-stu-id="35f79-154">Classes that implement `IPermission`:</span></span>

- <xref:System.Security.CodeAccessPermission?displayProperty=fullName>

<span data-ttu-id="35f79-155">Les classes qui dérivent de `CodeAccessPermission` :</span><span class="sxs-lookup"><span data-stu-id="35f79-155">Classes that derive from `CodeAccessPermission`:</span></span>

- <xref:System.Configuration.ConfigurationPermission?displayProperty=fullName>
- <xref:System.Data.Common.DBDataPermission?displayProperty=fullName>
- <xref:System.Data.Odbc.OdbcPermission?displayProperty=fullName>
- <xref:System.Data.OleDb.OleDbPermission?displayProperty=fullName>
- <xref:System.Data.SqlClient.SqlClientPermission?displayProperty=fullName>
- <xref:System.Data.OracleClient.OraclePermission?displayProperty=fullName>
- <xref:System.Drawing.Printing.PrintingPermission?displayProperty=fullName>
- <xref:System.Net.DnsPermission?displayProperty=fullName>
- <xref:System.Net.SocketPermission?displayProperty=fullName>
- <xref:System.Net.WebPermission?displayProperty=fullName>
- <xref:System.Net.Mail.SmtpPermission?displayProperty=fullName>
- <xref:System.Net.NetworkInformation.NetworkInformationPermission?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.PnrpPermission?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermission?displayProperty=fullName>
- <xref:System.Transactions.DistributedTransactionPermission?displayProperty=fullName>
- <xref:System.Web.AspNetHostingPermission?displayProperty=fullName>
- <xref:System.Xaml.Permissions.XamlLoadPermission?displayProperty=fullName>

<span data-ttu-id="35f79-156">Les classes qui dérivent de `ResourcePermissionBase` :</span><span class="sxs-lookup"><span data-stu-id="35f79-156">Classes that derive from `ResourcePermissionBase`:</span></span>

- <xref:System.Diagnostics.EventLogPermission?displayProperty=fullName>
- <xref:System.Diagnostics.PerformanceCounterPermission?displayProperty=fullName>
- <xref:System.DirectoryServices.DirectoryServicesPermission?displayProperty=fullName>
- <xref:System.ServiceProcess.ServiceControllerPermission?displayProperty=fullName>

<span data-ttu-id="35f79-157">Enums dans l' `System.Security.Permissions` espace de noms :</span><span class="sxs-lookup"><span data-stu-id="35f79-157">Enums in the `System.Security.Permissions` namespace:</span></span>

- <xref:System.Security.Permissions.DataProtectionPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.HostProtectionResource?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageContainment?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionAudio?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionImage?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionVideo?displayProperty=fullName>
- <xref:System.Security.Permissions.PermissionState?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermissionFlag?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionClipboard?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionWindow?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermissionLevel?displayProperty=fullName>

<span data-ttu-id="35f79-158">Classes et membres qui dépendent des types de sécurité d’accès du code :</span><span class="sxs-lookup"><span data-stu-id="35f79-158">Classes and members that depend on code access security types:</span></span>

- <xref:System.AppDomain.PermissionSet?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.AllowReversePInvokeCallsAttribute?displayProperty=fullName>
- <xref:System.Security.HostProtectionException?displayProperty=fullName>
- <xref:System.Security.Policy.FileCodeGroup?displayProperty=fullName>
- <xref:System.Security.Policy.StrongName?displayProperty=fullName>
- <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=fullName>
- [<span data-ttu-id="35f79-159">System. Security. Policy. ApplicationTrust. ApplicationTrust (PermissionSet, IEnumerable \<StrongName> )</span><span class="sxs-lookup"><span data-stu-id="35f79-159">System.Security.Policy.ApplicationTrust.ApplicationTrust(PermissionSet, IEnumerable\<StrongName>)</span></span>](/dotnet/api/system.security.policy.applicationtrust.-ctor#System_Security_Policy_ApplicationTrust__ctor_System_Security_PermissionSet_System_Collections_Generic_IEnumerable_System_Security_Policy_StrongName__)
- <xref:System.Security.Policy.ApplicationTrust.FullTrustAssemblies?displayProperty=fullName>
- <xref:System.Security.Policy.GacInstalled?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyStatement.%23ctor%2A?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.AddNamedPermissionSet(System.Security.NamedPermissionSet)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.ChangeNamedPermissionSet(System.String,System.Security.PermissionSet)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.GetNamedPermissionSet(System.String)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.RemoveNamedPermissionSet(System.String)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.RemoveNamedPermissionSet(System.Security.NamedPermissionSet)?displayProperty=nameWithType>
- <xref:System.Security.Policy.PolicyStatement.PermissionSet?displayProperty=fullName>
- <xref:System.Security.Policy.Publisher?displayProperty=fullName>
- <xref:System.Security.Policy.Site?displayProperty=fullName>
- <xref:System.Security.Policy.Url?displayProperty=fullName>
- <xref:System.Security.Policy.Zone?displayProperty=fullName>
- <xref:System.Security.SecurityManager?displayProperty=fullName>

### <a name="syslib0004"></a><span data-ttu-id="35f79-160">SYSLIB0004</span><span class="sxs-lookup"><span data-stu-id="35f79-160">SYSLIB0004</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

### <a name="syslib0005"></a><span data-ttu-id="35f79-161">SYSLIB0005</span><span class="sxs-lookup"><span data-stu-id="35f79-161">SYSLIB0005</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

### <a name="syslib0006"></a><span data-ttu-id="35f79-162">SYSLIB0006</span><span class="sxs-lookup"><span data-stu-id="35f79-162">SYSLIB0006</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

### <a name="syslib0007"></a><span data-ttu-id="35f79-163">SYSLIB0007</span><span class="sxs-lookup"><span data-stu-id="35f79-163">SYSLIB0007</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

### <a name="syslib0008"></a><span data-ttu-id="35f79-164">SYSLIB0008</span><span class="sxs-lookup"><span data-stu-id="35f79-164">SYSLIB0008</span></span>

- <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType>

### <a name="syslib0009"></a><span data-ttu-id="35f79-165">SYSLIB0009</span><span class="sxs-lookup"><span data-stu-id="35f79-165">SYSLIB0009</span></span>

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

### <a name="syslib0010"></a><span data-ttu-id="35f79-166">SYSLIB0010</span><span class="sxs-lookup"><span data-stu-id="35f79-166">SYSLIB0010</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

### <a name="syslib0011"></a><span data-ttu-id="35f79-167">SYSLIB0011</span><span class="sxs-lookup"><span data-stu-id="35f79-167">SYSLIB0011</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

### <a name="syslib0012"></a><span data-ttu-id="35f79-168">SYSLIB0012</span><span class="sxs-lookup"><span data-stu-id="35f79-168">SYSLIB0012</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>
