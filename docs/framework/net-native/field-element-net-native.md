---
title: Élément <Field> (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
ms.openlocfilehash: 2a63b88c399a999cd00750dee1614352cea10e80
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128421"
---
# <a name="field-element-net-native"></a><span data-ttu-id="9ee64-102">\<élément > Field (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="9ee64-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="9ee64-103">Applique la stratégie de réflexion runtime à un champ.</span><span class="sxs-lookup"><span data-stu-id="9ee64-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ee64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ee64-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ee64-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9ee64-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9ee64-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9ee64-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ee64-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="9ee64-107">Attributes</span></span>  
  
|<span data-ttu-id="9ee64-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="9ee64-108">Attribute</span></span>|<span data-ttu-id="9ee64-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="9ee64-109">Attribute type</span></span>|<span data-ttu-id="9ee64-110">Description</span><span class="sxs-lookup"><span data-stu-id="9ee64-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="9ee64-111">Général</span><span class="sxs-lookup"><span data-stu-id="9ee64-111">General</span></span>|<span data-ttu-id="9ee64-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="9ee64-112">Required attribute.</span></span> <span data-ttu-id="9ee64-113">Spécifie le nom du champ.</span><span class="sxs-lookup"><span data-stu-id="9ee64-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="9ee64-114">Réflexion</span><span class="sxs-lookup"><span data-stu-id="9ee64-114">Reflection</span></span>|<span data-ttu-id="9ee64-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="9ee64-115">Optional attribute.</span></span> <span data-ttu-id="9ee64-116">Contrôle la demande d'informations sur le champ ou l'énumération de celui-ci, mais ne permet pas d'effectuer un accès dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="9ee64-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="9ee64-117">Réflexion</span><span class="sxs-lookup"><span data-stu-id="9ee64-117">Reflection</span></span>|<span data-ttu-id="9ee64-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="9ee64-118">Optional attribute.</span></span> <span data-ttu-id="9ee64-119">Contrôle l'accès au champ au moment de l'exécution pour autoriser la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="9ee64-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="9ee64-120">Grâce à cette stratégie, un champ peut être défini ou récupéré dynamiquement au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="9ee64-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="9ee64-121">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="9ee64-121">Serialization</span></span>|<span data-ttu-id="9ee64-122">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="9ee64-122">Optional attribute.</span></span> <span data-ttu-id="9ee64-123">Contrôle l'accès à un champ au moment de l'exécution pour permettre aux instances de type d'être sérialisées par des bibliothèques, telles que le sérialiseur JSON Newtonsoft, ou d'être utilisées pour la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="9ee64-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="9ee64-124">Name (attribut)</span><span class="sxs-lookup"><span data-stu-id="9ee64-124">Name attribute</span></span>  
  
|<span data-ttu-id="9ee64-125">valeur</span><span class="sxs-lookup"><span data-stu-id="9ee64-125">Value</span></span>|<span data-ttu-id="9ee64-126">Description</span><span class="sxs-lookup"><span data-stu-id="9ee64-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9ee64-127">*nom_méthode*</span><span class="sxs-lookup"><span data-stu-id="9ee64-127">*method_name*</span></span>|<span data-ttu-id="9ee64-128">Nom du champ.</span><span class="sxs-lookup"><span data-stu-id="9ee64-128">The field name.</span></span> <span data-ttu-id="9ee64-129">Le type du champ est défini par l’élément [\<Type>](type-element-net-native.md) ou [\<TypeInstantiation>](typeinstantiation-element-net-native.md) parent.</span><span class="sxs-lookup"><span data-stu-id="9ee64-129">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="9ee64-130">Tous les autres attributs</span><span class="sxs-lookup"><span data-stu-id="9ee64-130">All other attributes</span></span>  
  
|<span data-ttu-id="9ee64-131">valeur</span><span class="sxs-lookup"><span data-stu-id="9ee64-131">Value</span></span>|<span data-ttu-id="9ee64-132">Description</span><span class="sxs-lookup"><span data-stu-id="9ee64-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9ee64-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="9ee64-133">*policy_setting*</span></span>|<span data-ttu-id="9ee64-134">Paramètre à appliquer à ce type de stratégie pour le champ.</span><span class="sxs-lookup"><span data-stu-id="9ee64-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="9ee64-135">Les valeurs possibles sont `Auto`, `Excluded`, `Included` et `Required`.</span><span class="sxs-lookup"><span data-stu-id="9ee64-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="9ee64-136">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="9ee64-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ee64-137">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9ee64-137">Child Elements</span></span>  
 <span data-ttu-id="9ee64-138">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="9ee64-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ee64-139">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9ee64-139">Parent Elements</span></span>  
  
|<span data-ttu-id="9ee64-140">Élément</span><span class="sxs-lookup"><span data-stu-id="9ee64-140">Element</span></span>|<span data-ttu-id="9ee64-141">Description</span><span class="sxs-lookup"><span data-stu-id="9ee64-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ee64-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="9ee64-142">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="9ee64-143">Applique la stratégie de réflexion à un type et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="9ee64-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="9ee64-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="9ee64-144">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="9ee64-145">Applique la stratégie de réflexion à un type générique construit et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="9ee64-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ee64-146">Notes</span><span class="sxs-lookup"><span data-stu-id="9ee64-146">Remarks</span></span>  
 <span data-ttu-id="9ee64-147">Si la stratégie d'un champ n'est pas définie explicitement, elle hérite la stratégie runtime de son élément parent.</span><span class="sxs-lookup"><span data-stu-id="9ee64-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee64-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ee64-148">See also</span></span>

- [<span data-ttu-id="9ee64-149">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="9ee64-149">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="9ee64-150">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="9ee64-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9ee64-151">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="9ee64-151">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
