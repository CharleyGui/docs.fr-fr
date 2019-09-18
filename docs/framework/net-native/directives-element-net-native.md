---
title: <Directives>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9ec9a09e2fc03adbfcff0d7e69489e37da6e4a5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049879"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="0cc3f-102">\<Directives >, élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0cc3f-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="0cc3f-103">Élément racine dans chaque fichier de directives Runtime pour .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="0cc3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cc3f-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="0cc3f-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="0cc3f-105">Attributes</span></span>  
  
|<span data-ttu-id="0cc3f-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="0cc3f-106">Attribute</span></span>|<span data-ttu-id="0cc3f-107">Description</span><span class="sxs-lookup"><span data-stu-id="0cc3f-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="0cc3f-108">Espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-108">The XML namespace.</span></span> <span data-ttu-id="0cc3f-109">Sa valeur est toujours **« http://schemas.microsoft.com/netfx/2013/01/metadata »** .</span><span class="sxs-lookup"><span data-stu-id="0cc3f-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="0cc3f-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0cc3f-110">Child elements</span></span>  
  
|<span data-ttu-id="0cc3f-111">Élément</span><span class="sxs-lookup"><span data-stu-id="0cc3f-111">Element</span></span>|<span data-ttu-id="0cc3f-112">Description</span><span class="sxs-lookup"><span data-stu-id="0cc3f-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0cc3f-113">\<Application></span><span class="sxs-lookup"><span data-stu-id="0cc3f-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="0cc3f-114">Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="0cc3f-115">\<Library></span><span class="sxs-lookup"><span data-stu-id="0cc3f-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="0cc3f-116">Définit l'assembly dont les types enfants et les membres de type nécessitent des métadonnées au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cc3f-117">Notes</span><span class="sxs-lookup"><span data-stu-id="0cc3f-117">Remarks</span></span>  
 <span data-ttu-id="0cc3f-118">Chaque fichier de directives runtime ne peut contenir qu'un seul élément `<Directives>`.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="0cc3f-119">L’élément `<Directives>` peut contenir zéro ou un élément [\<Application>](application-element-net-native.md), ainsi que zéro, un ou plusieurs éléments [\<Library>](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="0cc3f-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cc3f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cc3f-120">See also</span></span>

- [<span data-ttu-id="0cc3f-121">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0cc3f-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="0cc3f-122">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="0cc3f-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
