---
title: 'Procédure : Localiser des assemblys à l’aide de DEVPATH'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69913000"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="517f9-102">Procédure : Localiser des assemblys à l’aide de DEVPATH</span><span class="sxs-lookup"><span data-stu-id="517f9-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="517f9-103">Les développeurs peuvent souhaiter s’assurer qu’un assembly partagé qu’ils génèrent fonctionne correctement avec plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="517f9-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="517f9-104">Au lieu de placer continuellement l’assembly dans le Global Assembly Cache pendant le cycle de développement, le développeur peut créer une variable d’environnement DEVPATH qui pointe vers le répertoire de sortie de génération de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="517f9-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="517f9-105">Par exemple, supposons que vous génériez un assembly partagé appelé MySharedAssembly et que le répertoire de sortie soit C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="517f9-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="517f9-106">Vous pouvez placer C:\MySharedAssembly\Debug dans la variable DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="517f9-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="517f9-107">Vous devez ensuite spécifier l' [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) élément dans le fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="517f9-107">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="517f9-108">Cet élément indique à l’common language runtime d’utiliser DEVPATH pour localiser les assemblys.</span><span class="sxs-lookup"><span data-stu-id="517f9-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="517f9-109">L’assembly partagé doit être détectable par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="517f9-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="517f9-110">Pour spécifier un répertoire privé pour la résolution des références d’assembly, utilisez l' [ \<codeBase> élément](./file-schema/runtime/codebase-element.md) ou l' [ \<probing> élément](./file-schema/runtime/probing-element.md) dans un fichier de configuration, comme décrit dans spécification de l' [emplacement d’un assembly](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="517f9-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="517f9-111">Vous pouvez également placer l’assembly dans un sous-répertoire du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="517f9-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="517f9-112">Pour plus d’informations, consultez [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="517f9-112">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="517f9-113">Il s’agit d’une fonctionnalité avancée, conçue uniquement pour le développement.</span><span class="sxs-lookup"><span data-stu-id="517f9-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="517f9-114">L’exemple suivant montre comment faire en sorte que le runtime recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="517f9-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="517f9-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="517f9-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="517f9-116">La valeur par défaut de ce paramètre est false.</span><span class="sxs-lookup"><span data-stu-id="517f9-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="517f9-117">Utilisez ce paramètre uniquement au moment du développement.</span><span class="sxs-lookup"><span data-stu-id="517f9-117">Use this setting only at development time.</span></span> <span data-ttu-id="517f9-118">Le runtime ne vérifie pas les versions des assemblys avec nom fort qui se trouvent dans DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="517f9-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="517f9-119">Il utilise simplement le premier assembly qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="517f9-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="517f9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="517f9-120">See also</span></span>

- [<span data-ttu-id="517f9-121">Configuration des applications à l'aide de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="517f9-121">Configuring Apps by using Configuration Files</span></span>](index.md)
