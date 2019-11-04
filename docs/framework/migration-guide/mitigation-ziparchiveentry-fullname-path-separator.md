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
ms.openlocfilehash: 021d22e90ba39a4d01cf7d64588fab2d724b6640
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457737"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="1c5a0-102">Atténuation : Séparateur de chemin ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="1c5a0-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="1c5a0-103">À compter des applications qui ciblent .NET Framework 4.6.1, le séparateur de chemin utilisé dans la propriété <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> a été changé. Il ne s’agit plus de la barre oblique inverse (« \\ ») utilisée dans les versions antérieures du .NET Framework, mais de la barre oblique (« / »).</span><span class="sxs-lookup"><span data-stu-id="1c5a0-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="1c5a0-104">Les objets <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> sont créés en appelant l’une des surcharges de la méthode <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1c5a0-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="1c5a0-105">Impact</span><span class="sxs-lookup"><span data-stu-id="1c5a0-105">Impact</span></span>  
 <span data-ttu-id="1c5a0-106">L’implémentation .NET est ainsi conforme à la section 4.4.17.1 des [Spécifications relatives au format des fichiers ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) et permet aux archives ZIP d’être décompressées sur des systèmes non Windows.</span><span class="sxs-lookup"><span data-stu-id="1c5a0-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="1c5a0-107">Décompresser un fichier zip créé par une application qui cible une version antérieure de .NET Framework sur les systèmes d’exploitation non Windows tels que les ordinateurs Macintosh ne permet pas de conserver la structure de répertoire.</span><span class="sxs-lookup"><span data-stu-id="1c5a0-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="1c5a0-108">Par exemple, pour les ordinateurs Macintosh, cela crée un ensemble de fichiers dont le nom concatène le chemin d’accès, ainsi que toute barre oblique inverse (« \\ ») et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="1c5a0-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="1c5a0-109">Par conséquent, la structure de répertoires des fichiers décompressés n’est pas conservée.</span><span class="sxs-lookup"><span data-stu-id="1c5a0-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="1c5a0-110">L’impact de ce changement sur les fichiers .ZIP qui sont décompressés sur le système d’exploitation Windows par les API dans l’espace de noms <xref:System.IO> du .NET Framework doit être minimal, étant donné que ces API peuvent gérer sans problème aussi bien une barre oblique (« / ») qu’une barre oblique inverse (« \\ ») comme séparateur de chemin.</span><span class="sxs-lookup"><span data-stu-id="1c5a0-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="1c5a0-111">Atténuation</span><span class="sxs-lookup"><span data-stu-id="1c5a0-111">Mitigation</span></span>  
 <span data-ttu-id="1c5a0-112">Si ce comportement n’est pas souhaitable, vous pouvez choisir de l’annuler en ajoutant un paramètre de configuration pour la section [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="1c5a0-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="1c5a0-113">L’exemple suivant montre la section `<runtime>` et l’option d’annulation.</span><span class="sxs-lookup"><span data-stu-id="1c5a0-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="1c5a0-114">De plus, les applications qui ciblent des versions antérieures du .NET Framework mais qui s’exécutent sur .NET Framework 4.6.1 ou les versions ultérieures peuvent accepter ce comportement en ajoutant un paramètre de configuration à la section [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="1c5a0-114">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="1c5a0-115">L’exemple suivant montre la section `<runtime>` et l’option d’activation.</span><span class="sxs-lookup"><span data-stu-id="1c5a0-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c5a0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c5a0-116">See also</span></span>

- [<span data-ttu-id="1c5a0-117">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="1c5a0-117">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
- [<span data-ttu-id="1c5a0-118">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="1c5a0-118">Application compatibility</span></span>](application-compatibility.md)
