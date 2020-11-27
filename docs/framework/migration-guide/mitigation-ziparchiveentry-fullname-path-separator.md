---
title: 'Atténuation : Séparateur de chemin ZipArchiveEntry.FullName'
description: Découvrez comment le séparateur de chemin d’accès de la propriété ZipArchiveEntry. FullName a changé à partir des applications qui ciblent .NET Framework 4.6.1.
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 6e2c0908098f8487f7d429274fe7ad797bedfda1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283443"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="5bd18-103">Atténuation : Séparateur de chemin ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="5bd18-103">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="5bd18-104">À compter des applications qui ciblent le .NET Framework 4.6.1, le séparateur de chemin d’accès utilisé dans la <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> propriété a été modifié par rapport à la barre oblique inverse (« \\ ») utilisée dans les versions précédentes de .NET Framework à une barre oblique (« / »).</span><span class="sxs-lookup"><span data-stu-id="5bd18-104">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="5bd18-105">Les objets <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> sont créés en appelant l’une des surcharges de la méthode <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5bd18-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="5bd18-106">Impact</span><span class="sxs-lookup"><span data-stu-id="5bd18-106">Impact</span></span>  

 <span data-ttu-id="5bd18-107">L’implémentation .NET est ainsi conforme à la section 4.4.17.1 des [Spécifications relatives au format des fichiers ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) et permet aux archives ZIP d’être décompressées sur des systèmes non Windows.</span><span class="sxs-lookup"><span data-stu-id="5bd18-107">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="5bd18-108">La décompression d’un fichier zip créé par une application ciblant une version antérieure de .NET Framework sur des systèmes d’exploitation autres que Windows, comme MacOS, ne permet pas de conserver la structure de répertoires.</span><span class="sxs-lookup"><span data-stu-id="5bd18-108">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="5bd18-109">Par exemple, sur MacOS, il crée un ensemble de fichiers dont le nom de fichier concatène le chemin d’accès au répertoire, les caractères de barre oblique inverse (« \\ ») et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="5bd18-109">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="5bd18-110">Par conséquent, la structure de répertoires des fichiers décompressés n’est pas conservée.</span><span class="sxs-lookup"><span data-stu-id="5bd18-110">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="5bd18-111">Impact de cette modification sur. Les fichiers ZIP qui sont décompressés sur le système d’exploitation Windows par les API dans .NET Framework <xref:System.IO> espace de noms doivent être minimaux, puisque ces API peuvent gérer en toute transparence une barre oblique (« / ») ou une barre oblique inverse (« \\ ») comme séparateur de chemin.</span><span class="sxs-lookup"><span data-stu-id="5bd18-111">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="5bd18-112">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="5bd18-112">Mitigation</span></span>  

 <span data-ttu-id="5bd18-113">Si ce comportement n’est pas souhaitable, vous pouvez refuser en ajoutant un paramètre de configuration à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section de votre fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="5bd18-113">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="5bd18-114">L’exemple suivant montre la section `<runtime>` et l’option d’annulation.</span><span class="sxs-lookup"><span data-stu-id="5bd18-114">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="5bd18-115">En outre, les applications qui ciblent des versions antérieures de .NET Framework mais s’exécutent sur .NET Framework 4.6.1 et les versions ultérieures peuvent accepter ce comportement en ajoutant un paramètre de configuration à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="5bd18-115">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="5bd18-116">L’exemple suivant montre la section `<runtime>` et l’option d’activation.</span><span class="sxs-lookup"><span data-stu-id="5bd18-116">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5bd18-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bd18-117">See also</span></span>

- [<span data-ttu-id="5bd18-118">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="5bd18-118">Application compatibility</span></span>](application-compatibility.md)
