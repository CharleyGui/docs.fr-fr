---
title: <Directives> , Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 524c30872e218f6428491507bbfb4ca54b6061b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251098"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="c904e-102">\<Directives> , Élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="c904e-102">\<Directives> Element (.NET Native)</span></span>

<span data-ttu-id="c904e-103">Élément racine dans chaque fichier de directives Runtime pour .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c904e-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="c904e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c904e-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="c904e-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="c904e-105">Attributes</span></span>  
  
|<span data-ttu-id="c904e-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="c904e-106">Attribute</span></span>|<span data-ttu-id="c904e-107">Description</span><span class="sxs-lookup"><span data-stu-id="c904e-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="c904e-108">Espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="c904e-108">The XML namespace.</span></span> <span data-ttu-id="c904e-109">Sa valeur est toujours `http://schemas.microsoft.com/netfx/2013/01/metadata` .</span><span class="sxs-lookup"><span data-stu-id="c904e-109">Its value is always `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="c904e-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c904e-110">Child elements</span></span>  
  
|<span data-ttu-id="c904e-111">Élément</span><span class="sxs-lookup"><span data-stu-id="c904e-111">Element</span></span>|<span data-ttu-id="c904e-112">Description</span><span class="sxs-lookup"><span data-stu-id="c904e-112">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="c904e-113">Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion.</span><span class="sxs-lookup"><span data-stu-id="c904e-113">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="c904e-114">Définit l'assembly dont les types enfants et les membres de type nécessitent des métadonnées au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="c904e-114">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c904e-115">Notes</span><span class="sxs-lookup"><span data-stu-id="c904e-115">Remarks</span></span>  

 <span data-ttu-id="c904e-116">Chaque fichier de directives runtime ne peut contenir qu'un seul élément `<Directives>`.</span><span class="sxs-lookup"><span data-stu-id="c904e-116">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="c904e-117">L' `<Directives>` élément peut contenir zéro ou un [\<Application>](application-element-net-native.md) élément, et zéro, un ou plusieurs [\<Library>](library-element-net-native.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="c904e-117">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c904e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c904e-118">See also</span></span>

- [<span data-ttu-id="c904e-119">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="c904e-119">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="c904e-120">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="c904e-120">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
