---
title: Élément <Directives> (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: abe2e7221e0afb984a6178b12fabc36ea24deb35
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128472"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="7e6ef-102">\<, directives >, élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="7e6ef-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="7e6ef-103">Élément racine dans chaque fichier de directives Runtime pour .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="7e6ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e6ef-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="7e6ef-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="7e6ef-105">Attributes</span></span>  
  
|<span data-ttu-id="7e6ef-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="7e6ef-106">Attribute</span></span>|<span data-ttu-id="7e6ef-107">Description</span><span class="sxs-lookup"><span data-stu-id="7e6ef-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="7e6ef-108">Espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-108">The XML namespace.</span></span> <span data-ttu-id="7e6ef-109">Sa valeur est toujours **« http://schemas.microsoft.com/netfx/2013/01/metadata »** .</span><span class="sxs-lookup"><span data-stu-id="7e6ef-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="7e6ef-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7e6ef-110">Child elements</span></span>  
  
|<span data-ttu-id="7e6ef-111">Élément</span><span class="sxs-lookup"><span data-stu-id="7e6ef-111">Element</span></span>|<span data-ttu-id="7e6ef-112">Description</span><span class="sxs-lookup"><span data-stu-id="7e6ef-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e6ef-113">\<Application></span><span class="sxs-lookup"><span data-stu-id="7e6ef-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="7e6ef-114">Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="7e6ef-115">\<Library></span><span class="sxs-lookup"><span data-stu-id="7e6ef-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="7e6ef-116">Définit l'assembly dont les types enfants et les membres de type nécessitent des métadonnées au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e6ef-117">Notes</span><span class="sxs-lookup"><span data-stu-id="7e6ef-117">Remarks</span></span>  
 <span data-ttu-id="7e6ef-118">Chaque fichier de directives runtime ne peut contenir qu'un seul élément `<Directives>`.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="7e6ef-119">L’élément `<Directives>` peut contenir zéro ou un élément [\<Application>](application-element-net-native.md), ainsi que zéro, un ou plusieurs éléments [\<Library>](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="7e6ef-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e6ef-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e6ef-120">See also</span></span>

- [<span data-ttu-id="7e6ef-121">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="7e6ef-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7e6ef-122">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="7e6ef-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
