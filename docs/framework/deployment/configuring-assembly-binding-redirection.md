---
title: Configuration de la liaison d’assembly
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: 5b24d99aa23358272eecd042c40001413965d7f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181681"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="d099d-102">Configuration de la liaison d’assembly</span><span class="sxs-lookup"><span data-stu-id="d099d-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="d099d-103">Par défaut, les applications utilisent le jeu d'assemblys .NET Framework qui est fourni avec la version du runtime utilisée pour compiler l'application.</span><span class="sxs-lookup"><span data-stu-id="d099d-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="d099d-104">Vous pouvez utiliser l’attribut **appliesTo** sur l’élément [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) dans un fichier de configuration d’application pour rediriger les références de liaison d’assembly vers une version spécifique des assemblys du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d099d-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="d099d-105">Cet attribut facultatif utilise un numéro de version .NET Framework pour indiquer la version à laquelle il s'applique.</span><span class="sxs-lookup"><span data-stu-id="d099d-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="d099d-106">Si l’attribut **appliesTo** n’est pas spécifié, l’élément **\<assemblyBinding>** s’applique à toutes les versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d099d-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d099d-107">L’attribut **appliesTo** a été introduit dans le .NET Framework 1.1. Il est ignoré dans le .NET Framework 1.0.</span><span class="sxs-lookup"><span data-stu-id="d099d-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="d099d-108">Cela signifie \*\* \<\*\* que tous les éléments de>de assemblage sont appliqués lors de l’utilisation de la version cadre .NET 1.0, même si un attribut **appliqueTo** est spécifié.</span><span class="sxs-lookup"><span data-stu-id="d099d-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d099d-109">Utilisez l’attribut **appliesTo** pour limiter la redirection de liaison d’assembly vers une version spécifique du runtime.</span><span class="sxs-lookup"><span data-stu-id="d099d-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="d099d-110">Par exemple, pour rediriger la liaison d’assembly pour un assembly du .NET Framework 1.0, vous devez inclure le code XML suivant dans votre fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="d099d-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="d099d-111">\*\* \<L’assemblageBinding>\*\* éléments sont sensibles à l’ordre.</span><span class="sxs-lookup"><span data-stu-id="d099d-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="d099d-112">Ainsi, vous devez d’abord entrer les informations de redirection des liaisons des assemblys du .NET Framework 1.0, puis celles des assemblys du .NET Framework 1.1.</span><span class="sxs-lookup"><span data-stu-id="d099d-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="d099d-113">Enfin, vous devez entrer les informations de redirection des liaisons d'assembly pour toutes les redirections d'assembly du .NET Framework qui n'utilisent pas d'attribut **appliesTo** et qui s'appliquent donc à toutes les versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d099d-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="d099d-114">En cas de conflit de redirection, la première instruction de redirection correspondante dans le fichier de configuration est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d099d-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="d099d-115">Par exemple, pour rediriger une référence à un assembly du .NET Framework 1.0 et une autre à un assembly du .NET Framework 1.1, utilisez le modèle indiqué dans le pseudo-code suivant.</span><span class="sxs-lookup"><span data-stu-id="d099d-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">
  <!-- .NET Framework version 1.0 redirects here. -->
</assemblyBinding>
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">
  <!-- .NET Framework version 1.1 redirects here. -->
</assemblyBinding>
  
<assemblyBinding xmlns="...">
  <!-- Redirects meant for all versions of the .NET Framework. -->
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="d099d-116">Débogage des erreurs de fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="d099d-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="d099d-117">Le runtime analyse les fichiers de configuration au moment de la création d'un domaine d'application, puis il charge le code dans ce domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="d099d-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="d099d-118">Le common language runtime gère les erreurs dans un fichier de configuration en ignorant l'entrée.</span><span class="sxs-lookup"><span data-stu-id="d099d-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="d099d-119">Le runtime ignore tout le fichier de configuration si celui-ci contient du code XML incorrectement formé.</span><span class="sxs-lookup"><span data-stu-id="d099d-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="d099d-120">En présence de code XML non valide, seules les sections non valides sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="d099d-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="d099d-121">Vous pouvez déterminer si un fichier de configuration est actuellement utilisé en vérifiant si des redirections de liaison d’assembly ont lieu.</span><span class="sxs-lookup"><span data-stu-id="d099d-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="d099d-122">Utilisez la [Visionneuse du journal de liaison d’assembly (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) pour voir quels assemblys sont chargés.</span><span class="sxs-lookup"><span data-stu-id="d099d-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="d099d-123">Pour voir toutes les liaisons d’assembly, vous devez ajouter une entrée pour **ForceLog** dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="d099d-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d099d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d099d-124">See also</span></span>

- [<span data-ttu-id="d099d-125">Comment : activer et désactiver la redirection de liaison automatique</span><span class="sxs-lookup"><span data-stu-id="d099d-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
