---
title: 'Atténuation : Séparateur de chemin ZipArchiveEntry.FullName'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 3f6c7f258fd5dbf01db4d79b73b88ddd7484f9b2
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102617"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="90fc0-102">Atténuation : Séparateur de chemin ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="90fc0-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="90fc0-103">En commençant par les applications qui ciblent le cadre .NET 4.6.1, le séparateur de chemin utilisé dans la <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> propriété a changé de la barre oblique inverse ("\\") utilisé dans les versions précédentes de .NET Framework à une barre oblique avant ("/").</span><span class="sxs-lookup"><span data-stu-id="90fc0-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="90fc0-104">Les objets <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> sont créés en appelant l’une des surcharges de la méthode <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="90fc0-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="90fc0-105">Impact</span><span class="sxs-lookup"><span data-stu-id="90fc0-105">Impact</span></span>  
 <span data-ttu-id="90fc0-106">L’implémentation .NET est ainsi conforme à la section 4.4.17.1 des [Spécifications relatives au format des fichiers ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) et permet aux archives ZIP d’être décompressées sur des systèmes non Windows.</span><span class="sxs-lookup"><span data-stu-id="90fc0-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="90fc0-107">Décompresser un fichier zip créé par une application qui cible une version précédente de .NET Framework sur les systèmes d’exploitation non Windows tels que MacOS ne parvient pas à préserver la structure d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="90fc0-107">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="90fc0-108">Par exemple, sur MacOS, il crée un ensemble de fichiers dont le nom de\\fichier concatenates le chemin de l’annuaire, tout backslash (" ") caractères, et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="90fc0-108">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="90fc0-109">Par conséquent, la structure de répertoires des fichiers décompressés n’est pas conservée.</span><span class="sxs-lookup"><span data-stu-id="90fc0-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="90fc0-110">L’impact de ce changement sur . Les fichiers ZIP qui sont décompressés sur le <xref:System.IO> système d’exploitation Windows par les API dans l’espace nom cadre .NET devraient\\être minimes, puisque ces API peuvent gérer de manière transparente soit une barre oblique ("/") ou un backslash (" " ) comme caractère de séparateur de chemin.</span><span class="sxs-lookup"><span data-stu-id="90fc0-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="90fc0-111">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="90fc0-111">Mitigation</span></span>  
 <span data-ttu-id="90fc0-112">Si ce comportement n’est pas souhaitable, vous pouvez vous [ \<](../configure-apps/file-schema/runtime/runtime-element.md) désinscrier en ajoutant un paramètre de configuration à la section de configuration>de votre fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="90fc0-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="90fc0-113">L’exemple suivant montre la section `<runtime>` et l’option d’annulation.</span><span class="sxs-lookup"><span data-stu-id="90fc0-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="90fc0-114">En outre, les applications qui ciblent les versions précédentes de .NET Framework mais sont en cours d’exécution sur .NET [ \<](../configure-apps/file-schema/runtime/runtime-element.md) Framework 4.6.1 et les versions ultérieures peuvent opter pour ce comportement en ajoutant un paramètre de configuration à la section de temps d’exécution>du fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="90fc0-114">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="90fc0-115">L’exemple suivant montre la section `<runtime>` et l’option d’activation.</span><span class="sxs-lookup"><span data-stu-id="90fc0-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="90fc0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90fc0-116">See also</span></span>

- [<span data-ttu-id="90fc0-117">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="90fc0-117">Application compatibility</span></span>](application-compatibility.md)
