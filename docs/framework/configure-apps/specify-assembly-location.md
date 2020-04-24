---
title: Spécification de l'emplacement d'un assembly
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646031"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="6201e-102">Spécification de l'emplacement d'un assembly</span><span class="sxs-lookup"><span data-stu-id="6201e-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="6201e-103">Il y a deux façons de spécifier l’emplacement d’une assemblée :</span><span class="sxs-lookup"><span data-stu-id="6201e-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="6201e-104">Utilisation du [ \<codeBase>](./file-schema/runtime/codebase-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="6201e-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="6201e-105">Utilisation de [ \<l’élément de sondage>.](./file-schema/runtime/probing-element.md)</span><span class="sxs-lookup"><span data-stu-id="6201e-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="6201e-106">Vous pouvez également utiliser [l’outil de configuration cadre .NET (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) pour spécifier les emplacements d’assemblage ou spécifier les emplacements de l’heure d’exécution de langue commune pour sonder les assemblages.</span><span class="sxs-lookup"><span data-stu-id="6201e-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="6201e-107">Utilisation \<du codeBase> Element</span><span class="sxs-lookup"><span data-stu-id="6201e-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="6201e-108">Vous pouvez utiliser le \*\* \<codeBase>\*\* élément uniquement dans la configuration de la machine ou les fichiers de stratégie de l’éditeur qui rediriger également la version d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="6201e-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="6201e-109">Lorsque le temps d’exécution détermine la version d’assemblage à utiliser, il applique le paramètre de base de code du fichier qui détermine la version.</span><span class="sxs-lookup"><span data-stu-id="6201e-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="6201e-110">Si aucune base de code n’est indiquée, les sondes de temps d’exécution pour l’assemblage de la manière normale.</span><span class="sxs-lookup"><span data-stu-id="6201e-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="6201e-111">Pour plus de détails, voir [Comment les assemblages De localisation de Runtime](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6201e-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="6201e-112">L’exemple suivant montre comment spécifier l’emplacement d’une assemblée.</span><span class="sxs-lookup"><span data-stu-id="6201e-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="6201e-113">**L’attribut de version** est exigé pour toutes les assemblées nommées fort, mais doit être omise pour les assemblées qui ne sont pas nommées fort.</span><span class="sxs-lookup"><span data-stu-id="6201e-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="6201e-114">Le \*\* \<codeBase>\*\* élément nécessite l’attribut **href.**</span><span class="sxs-lookup"><span data-stu-id="6201e-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="6201e-115">Vous ne pouvez pas spécifier les plages de version dans l’élément \*\* \<codeBase>.\*\*</span><span class="sxs-lookup"><span data-stu-id="6201e-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6201e-116">Si vous fournissez un indice de base de code pour une assemblée qui n’est pas solidement nommée, l’indice doit indiquer la base d’application ou une sous-direction de l’annuaire de base d’application.</span><span class="sxs-lookup"><span data-stu-id="6201e-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="6201e-117">Utilisation \<de l’élément> de sondage</span><span class="sxs-lookup"><span data-stu-id="6201e-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="6201e-118">Le temps d’exécution localise les assemblages qui n’ont pas de base de code en sondant.</span><span class="sxs-lookup"><span data-stu-id="6201e-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="6201e-119">Pour plus d’informations sur l’enquête, voir [Comment les assemblages Runtime Locates](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6201e-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="6201e-120">Vous pouvez [ \<](./file-schema/runtime/probing-element.md) utiliser l’élément de sondage>dans le fichier de configuration d’application pour spécifier les sous-directions que l’heure d’exécution doit rechercher lors de la localisation d’un assemblage.</span><span class="sxs-lookup"><span data-stu-id="6201e-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="6201e-121">L’exemple suivant montre comment spécifier les répertoires que l’heure d’exécution doit rechercher.</span><span class="sxs-lookup"><span data-stu-id="6201e-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="6201e-122">**L’attribut PrivatePath** contient les répertoires que le temps d’exécution doit rechercher des assemblages.</span><span class="sxs-lookup"><span data-stu-id="6201e-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="6201e-123">Si l’application est située à C : Fichiers de programme MyApp, l’exécution recherchera des assemblages qui ne spécifient pas une base de code dans C : Fichiers de programme- MyApp’Bin, C : Fichiers de programme -MyApp’Bin2-Subbin, et C : Fichiers de programme-MyApp-Bin3.</span><span class="sxs-lookup"><span data-stu-id="6201e-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="6201e-124">Les répertoires spécifiés dans **privatePath** doivent être des sous-directeurs de l’annuaire de base d’application.</span><span class="sxs-lookup"><span data-stu-id="6201e-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6201e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6201e-125">See also</span></span>

- [<span data-ttu-id="6201e-126">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="6201e-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="6201e-127">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="6201e-127">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="6201e-128">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="6201e-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="6201e-129">Configuration des applications à l'aide de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="6201e-129">Configuring Apps by using Configuration Files</span></span>](index.md)
