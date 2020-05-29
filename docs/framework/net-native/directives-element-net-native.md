---
title: <Directives>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 0c6ebb8954e80f3f6dc6733f0e9d76094477689b
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202384"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="82d03-102">\<Directives>, Élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="82d03-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="82d03-103">Élément racine dans chaque fichier de directives Runtime pour .NET Native.</span><span class="sxs-lookup"><span data-stu-id="82d03-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="82d03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82d03-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="82d03-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="82d03-105">Attributes</span></span>  
  
|<span data-ttu-id="82d03-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="82d03-106">Attribute</span></span>|<span data-ttu-id="82d03-107">Description</span><span class="sxs-lookup"><span data-stu-id="82d03-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="82d03-108">Espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="82d03-108">The XML namespace.</span></span> <span data-ttu-id="82d03-109">Sa valeur est toujours `http://schemas.microsoft.com/netfx/2013/01/metadata` .</span><span class="sxs-lookup"><span data-stu-id="82d03-109">Its value is always `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="82d03-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="82d03-110">Child elements</span></span>  
  
|<span data-ttu-id="82d03-111">Élément</span><span class="sxs-lookup"><span data-stu-id="82d03-111">Element</span></span>|<span data-ttu-id="82d03-112">Description</span><span class="sxs-lookup"><span data-stu-id="82d03-112">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="82d03-113">Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion.</span><span class="sxs-lookup"><span data-stu-id="82d03-113">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="82d03-114">Définit l'assembly dont les types enfants et les membres de type nécessitent des métadonnées au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="82d03-114">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82d03-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="82d03-115">Remarks</span></span>  
 <span data-ttu-id="82d03-116">Chaque fichier de directives runtime ne peut contenir qu'un seul élément `<Directives>`.</span><span class="sxs-lookup"><span data-stu-id="82d03-116">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="82d03-117">L' `<Directives>` élément peut contenir zéro ou un [\<Application>](application-element-net-native.md) élément, et zéro, un ou plusieurs [\<Library>](library-element-net-native.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="82d03-117">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d03-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82d03-118">See also</span></span>

- [<span data-ttu-id="82d03-119">Informations de référence sur le fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="82d03-119">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="82d03-120">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="82d03-120">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
