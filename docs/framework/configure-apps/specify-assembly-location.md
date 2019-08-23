---
title: Spécification de l'emplacement d'un assembly
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: 43cd1d0edbb607f69f27661aae3372e93564b3b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932333"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="fcdaa-102">Spécification de l'emplacement d'un assembly</span><span class="sxs-lookup"><span data-stu-id="fcdaa-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="fcdaa-103">Il existe deux façons de spécifier l’emplacement d’un assembly:</span><span class="sxs-lookup"><span data-stu-id="fcdaa-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="fcdaa-104">À l' [ \<](./file-schema/runtime/codebase-element.md) aide de l’élément CodeBase >.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="fcdaa-105">À l’aide de l’élément de [ \<> de détection](./file-schema/runtime/probing-element.md) .</span><span class="sxs-lookup"><span data-stu-id="fcdaa-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="fcdaa-106">Vous pouvez également utiliser l' [outil de Configuration .NET Framework (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) pour spécifier des emplacements d’assembly ou spécifier des emplacements pour le Common Language Runtime pour détecter les assemblys.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="fcdaa-107">Utilisation de \<l’élément CodeBase ></span><span class="sxs-lookup"><span data-stu-id="fcdaa-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="fcdaa-108">Vous pouvez utiliser l'  **\<** élément CodeBase > uniquement dans la configuration de l’ordinateur ou dans les fichiers de stratégie d’éditeur qui redirigent également la version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="fcdaa-109">Lorsque le runtime détermine la version de l’assembly à utiliser, il applique le paramètre de base du code à partir du fichier qui détermine la version.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="fcdaa-110">Si aucune base de code n’est indiquée, le runtime détecte l’assembly de manière normale.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="fcdaa-111">Pour plus d’informations, consultez [Comment le runtime localise les assemblys](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="fcdaa-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="fcdaa-112">L’exemple suivant montre comment spécifier l’emplacement d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="fcdaa-113">L’attribut **version** est requis pour tous les assemblys avec nom fort, mais doit être omis pour les assemblys qui ne portent pas un nom fort.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="fcdaa-114">**L'\<** élément CodeBase > nécessite l’attribut **href** .</span><span class="sxs-lookup"><span data-stu-id="fcdaa-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="fcdaa-115">Vous ne pouvez pas spécifier de plages  **\<** de versions dans l’élément CodeBase >.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcdaa-116">Si vous fournissez un indicateur de base de code pour un assembly qui n’a pas un nom fort, l’indicateur doit pointer vers la base de l’application ou vers un sous-répertoire du répertoire de base de l’application.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="fcdaa-117">Utilisation de \<l’élément de > de détection</span><span class="sxs-lookup"><span data-stu-id="fcdaa-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="fcdaa-118">Le runtime localise les assemblys qui n’ont pas de base de code en procédant à une détection.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="fcdaa-119">Pour plus d’informations sur la détection, voir [Comment le runtime localise les assemblys](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="fcdaa-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="fcdaa-120">Vous pouvez utiliser l' [ \<](./file-schema/runtime/probing-element.md) élément de > de détection dans le fichier de configuration de l’application pour spécifier les sous-répertoires que le runtime doit rechercher lors de la localisation d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="fcdaa-121">L’exemple suivant montre comment spécifier les répertoires dans lesquels le runtime doit effectuer des recherches.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="fcdaa-122">L’attribut **privatePath** contient les répertoires dans lesquels le runtime doit rechercher des assemblys.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="fcdaa-123">Si l’application se trouve dans C:\Program Files\MyApp, le runtime recherche les assemblys qui ne spécifient pas de base de code dans C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin et C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="fcdaa-124">Les répertoires spécifiés dans **privatePath** doivent être des sous-répertoires du répertoire de base de l’application.</span><span class="sxs-lookup"><span data-stu-id="fcdaa-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcdaa-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcdaa-125">See also</span></span>

- [<span data-ttu-id="fcdaa-126">Assemblys dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="fcdaa-126">Assemblies in the Common Language Runtime</span></span>](../app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="fcdaa-127">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="fcdaa-127">Programming with Assemblies</span></span>](../app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="fcdaa-128">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="fcdaa-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="fcdaa-129">Configuration d’applications à l’aide de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="fcdaa-129">Configuring Apps by using Configuration Files</span></span>](index.md)
