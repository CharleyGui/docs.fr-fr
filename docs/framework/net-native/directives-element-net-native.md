---
title: <Directives>Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 49c1aaf005b80a6c1c1fa382eebc2cb0dbfa4be7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181056"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="7bf75-102">\<Directives> Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="7bf75-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="7bf75-103">L’élément racine dans chaque fichier de directives runtime pour .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7bf75-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="7bf75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bf75-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="7bf75-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="7bf75-105">Attributes</span></span>  
  
|<span data-ttu-id="7bf75-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="7bf75-106">Attribute</span></span>|<span data-ttu-id="7bf75-107">Description</span><span class="sxs-lookup"><span data-stu-id="7bf75-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="7bf75-108">Espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="7bf75-108">The XML namespace.</span></span> <span data-ttu-id="7bf75-109">Sa valeur est toujours **"http://schemas.microsoft.com/netfx/2013/01/metadata.**</span><span class="sxs-lookup"><span data-stu-id="7bf75-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="7bf75-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7bf75-110">Child elements</span></span>  
  
|<span data-ttu-id="7bf75-111">Élément</span><span class="sxs-lookup"><span data-stu-id="7bf75-111">Element</span></span>|<span data-ttu-id="7bf75-112">Description</span><span class="sxs-lookup"><span data-stu-id="7bf75-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bf75-113">\<>d’application</span><span class="sxs-lookup"><span data-stu-id="7bf75-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="7bf75-114">Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion.</span><span class="sxs-lookup"><span data-stu-id="7bf75-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="7bf75-115">\<>de bibliothèque</span><span class="sxs-lookup"><span data-stu-id="7bf75-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="7bf75-116">Définit l'assembly dont les types enfants et les membres de type nécessitent des métadonnées au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="7bf75-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bf75-117">Notes </span><span class="sxs-lookup"><span data-stu-id="7bf75-117">Remarks</span></span>  
 <span data-ttu-id="7bf75-118">Chaque fichier de directives runtime ne peut contenir qu'un seul élément `<Directives>`.</span><span class="sxs-lookup"><span data-stu-id="7bf75-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="7bf75-119">L’élément `<Directives>` peut contenir [ \<](application-element-net-native.md) zéro ou une application>élément, et zéro, un ou plus [ \<de>](library-element-net-native.md) éléments de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="7bf75-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf75-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bf75-120">See also</span></span>

- [<span data-ttu-id="7bf75-121">Informations de référence sur le fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="7bf75-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7bf75-122">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="7bf75-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
