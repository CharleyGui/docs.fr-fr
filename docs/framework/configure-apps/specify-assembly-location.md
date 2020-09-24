---
title: Spécification de l'emplacement d'un assembly
description: Consultez Comment spécifier l’emplacement d’un assembly dans .NET à l’aide de l’élément CodeBase ou de l’élément de détection dans un fichier de configuration XML.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: 6f9e41584ca36fcead06b73a485cb879c45705fa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166883"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="2b01a-103">Spécification de l'emplacement d'un assembly</span><span class="sxs-lookup"><span data-stu-id="2b01a-103">Specifying an Assembly's Location</span></span>

<span data-ttu-id="2b01a-104">Il existe deux façons de spécifier l’emplacement d’un assembly :</span><span class="sxs-lookup"><span data-stu-id="2b01a-104">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="2b01a-105">À l’aide de l' [\<codeBase>](./file-schema/runtime/codebase-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="2b01a-105">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="2b01a-106">À l’aide de l' [\<probing>](./file-schema/runtime/probing-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="2b01a-106">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="2b01a-107">Vous pouvez également utiliser l' [outil de Configuration .NET Framework (Mscorcfg. msc)](/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) pour spécifier des emplacements d’assembly ou spécifier des emplacements pour le Common Language Runtime pour détecter les assemblys.</span><span class="sxs-lookup"><span data-stu-id="2b01a-107">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="2b01a-108">Utilisation de l' \<codeBase> élément</span><span class="sxs-lookup"><span data-stu-id="2b01a-108">Using the \<codeBase> Element</span></span>  

 <span data-ttu-id="2b01a-109">Vous pouvez utiliser l' **\<codeBase>** élément uniquement dans la configuration de l’ordinateur ou dans les fichiers de stratégie de l’éditeur qui redirigent également la version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="2b01a-109">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="2b01a-110">Lorsque le runtime détermine la version de l’assembly à utiliser, il applique le paramètre de base du code à partir du fichier qui détermine la version.</span><span class="sxs-lookup"><span data-stu-id="2b01a-110">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="2b01a-111">Si aucune base de code n’est indiquée, le runtime détecte l’assembly de manière normale.</span><span class="sxs-lookup"><span data-stu-id="2b01a-111">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="2b01a-112">Pour plus d’informations, consultez [Comment le runtime localise les assemblys](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="2b01a-112">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="2b01a-113">L’exemple suivant montre comment spécifier l’emplacement d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="2b01a-113">The following example shows how to specify an assembly's location.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="2b01a-114">L’attribut **version** est requis pour tous les assemblys avec nom fort, mais doit être omis pour les assemblys qui ne portent pas un nom fort.</span><span class="sxs-lookup"><span data-stu-id="2b01a-114">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="2b01a-115">L' **\<codeBase>** élément requiert l’attribut **href** .</span><span class="sxs-lookup"><span data-stu-id="2b01a-115">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="2b01a-116">Vous ne pouvez pas spécifier de plages de versions dans l' **\<codeBase>** élément.</span><span class="sxs-lookup"><span data-stu-id="2b01a-116">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b01a-117">Si vous fournissez un indicateur de base de code pour un assembly qui n’a pas un nom fort, l’indicateur doit pointer vers la base de l’application ou vers un sous-répertoire du répertoire de base de l’application.</span><span class="sxs-lookup"><span data-stu-id="2b01a-117">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="2b01a-118">Utilisation de l' \<probing> élément</span><span class="sxs-lookup"><span data-stu-id="2b01a-118">Using the \<probing> Element</span></span>  

 <span data-ttu-id="2b01a-119">Le runtime localise les assemblys qui n’ont pas de base de code en procédant à une détection.</span><span class="sxs-lookup"><span data-stu-id="2b01a-119">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="2b01a-120">Pour plus d’informations sur la détection, voir [Comment le runtime localise les assemblys](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="2b01a-120">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="2b01a-121">Vous pouvez utiliser l' [\<probing>](./file-schema/runtime/probing-element.md) élément dans le fichier de configuration de l’application pour spécifier les sous-répertoires que le runtime doit rechercher lors de la localisation d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="2b01a-121">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="2b01a-122">L’exemple suivant montre comment spécifier les répertoires dans lesquels le runtime doit effectuer des recherches.</span><span class="sxs-lookup"><span data-stu-id="2b01a-122">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="2b01a-123">L’attribut **privatePath** contient les répertoires dans lesquels le runtime doit rechercher des assemblys.</span><span class="sxs-lookup"><span data-stu-id="2b01a-123">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="2b01a-124">Si l’application se trouve dans C:\Program Files\MyApp, le runtime recherche les assemblys qui ne spécifient pas de base de code dans C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin et C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="2b01a-124">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="2b01a-125">Les répertoires spécifiés dans **privatePath** doivent être des sous-répertoires du répertoire de base de l’application.</span><span class="sxs-lookup"><span data-stu-id="2b01a-125">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b01a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b01a-126">See also</span></span>

- [<span data-ttu-id="2b01a-127">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="2b01a-127">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="2b01a-128">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="2b01a-128">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="2b01a-129">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="2b01a-129">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="2b01a-130">Configuration des applications à l'aide de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="2b01a-130">Configuring Apps by using Configuration Files</span></span>](index.md)
