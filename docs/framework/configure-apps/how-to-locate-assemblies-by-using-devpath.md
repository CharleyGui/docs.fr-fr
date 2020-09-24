---
title: 'Procédure : Localiser des assemblys à l’aide de DEVPATH'
description: Testez le bon fonctionnement d’un assembly partagé avec de nombreuses applications dans .NET en utilisant un fichier de configuration d’ordinateur XML et la variable d’environnement DEVPATH.
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 8ae807e46b11d2adb06d6af0c86e1c7297caa0c0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161982"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="b12d5-103">Procédure : Localiser des assemblys à l’aide de DEVPATH</span><span class="sxs-lookup"><span data-stu-id="b12d5-103">How to: Locate Assemblies by Using DEVPATH</span></span>

<span data-ttu-id="b12d5-104">Les développeurs peuvent souhaiter s’assurer qu’un assembly partagé qu’ils génèrent fonctionne correctement avec plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="b12d5-104">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="b12d5-105">Au lieu de placer continuellement l’assembly dans le Global Assembly Cache pendant le cycle de développement, le développeur peut créer une variable d’environnement DEVPATH qui pointe vers le répertoire de sortie de génération de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b12d5-105">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="b12d5-106">Par exemple, supposons que vous génériez un assembly partagé appelé MySharedAssembly et que le répertoire de sortie soit C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="b12d5-106">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="b12d5-107">Vous pouvez placer C:\MySharedAssembly\Debug dans la variable DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="b12d5-107">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="b12d5-108">Vous devez ensuite spécifier l' [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) élément dans le fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b12d5-108">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="b12d5-109">Cet élément indique à l’common language runtime d’utiliser DEVPATH pour localiser les assemblys.</span><span class="sxs-lookup"><span data-stu-id="b12d5-109">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="b12d5-110">L’assembly partagé doit être détectable par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="b12d5-110">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="b12d5-111">Pour spécifier un répertoire privé pour la résolution des références d’assembly, utilisez l' [ \<codeBase> élément](./file-schema/runtime/codebase-element.md) ou l' [ \<probing> élément](./file-schema/runtime/probing-element.md) dans un fichier de configuration, comme décrit dans spécification de l' [emplacement d’un assembly](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="b12d5-111">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="b12d5-112">Vous pouvez également placer l’assembly dans un sous-répertoire du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="b12d5-112">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="b12d5-113">Pour plus d’informations, consultez [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="b12d5-113">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b12d5-114">Il s’agit d’une fonctionnalité avancée, conçue uniquement pour le développement.</span><span class="sxs-lookup"><span data-stu-id="b12d5-114">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="b12d5-115">L’exemple suivant montre comment faire en sorte que le runtime recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="b12d5-115">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b12d5-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="b12d5-116">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="b12d5-117">La valeur par défaut de ce paramètre est false.</span><span class="sxs-lookup"><span data-stu-id="b12d5-117">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b12d5-118">Utilisez ce paramètre uniquement au moment du développement.</span><span class="sxs-lookup"><span data-stu-id="b12d5-118">Use this setting only at development time.</span></span> <span data-ttu-id="b12d5-119">Le runtime ne vérifie pas les versions des assemblys avec nom fort qui se trouvent dans DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="b12d5-119">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="b12d5-120">Il utilise simplement le premier assembly qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="b12d5-120">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12d5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b12d5-121">See also</span></span>

- [<span data-ttu-id="b12d5-122">Configuration des applications à l'aide de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b12d5-122">Configuring Apps by using Configuration Files</span></span>](index.md)
