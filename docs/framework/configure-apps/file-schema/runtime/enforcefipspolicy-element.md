---
title: Élément <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb28eddf7e9f13bceaf47de28633073f59f3920d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663746"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="b5f91-102">\<enforceFIPSPolicy >, élément</span><span class="sxs-lookup"><span data-stu-id="b5f91-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="b5f91-103">Indique s’il faut appliquer la condition de configuration d’ordinateur selon laquelle les algorithmes de chiffrement doivent être conformes aux normes FIPS (Federal Information Processing Standard).</span><span class="sxs-lookup"><span data-stu-id="b5f91-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="b5f91-104">\<Élément de > de configuration</span><span class="sxs-lookup"><span data-stu-id="b5f91-104">\<configuration> Element</span></span>  
<span data-ttu-id="b5f91-105">\<Élément > du Runtime</span><span class="sxs-lookup"><span data-stu-id="b5f91-105">\<runtime> Element</span></span>  
<span data-ttu-id="b5f91-106">\<enforceFIPSPolicy >, élément</span><span class="sxs-lookup"><span data-stu-id="b5f91-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5f91-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5f91-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5f91-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b5f91-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b5f91-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b5f91-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5f91-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b5f91-110">Attributes</span></span>  
  
|<span data-ttu-id="b5f91-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="b5f91-111">Attribute</span></span>|<span data-ttu-id="b5f91-112">Description</span><span class="sxs-lookup"><span data-stu-id="b5f91-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5f91-113">enabled</span><span class="sxs-lookup"><span data-stu-id="b5f91-113">enabled</span></span>|<span data-ttu-id="b5f91-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="b5f91-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="b5f91-115">Spécifie s’il faut activer la mise en application d’une exigence de configuration d’ordinateur que les algorithmes de chiffrement doivent être conformes à la norme FIPS.</span><span class="sxs-lookup"><span data-stu-id="b5f91-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b5f91-116">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="b5f91-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="b5f91-117">`Value`</span><span class="sxs-lookup"><span data-stu-id="b5f91-117">Value</span></span>|<span data-ttu-id="b5f91-118">Description</span><span class="sxs-lookup"><span data-stu-id="b5f91-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="b5f91-119">Si votre ordinateur est configuré pour exiger que les algorithmes de chiffrement soient compatibles FIPS, cette exigence est appliquée.</span><span class="sxs-lookup"><span data-stu-id="b5f91-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="b5f91-120">Si une classe implémente un algorithme qui n’est pas compatible avec FIPS, les constructeurs ou `Create` les méthodes de cette classe lèvent des exceptions lorsqu’elles sont exécutées sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b5f91-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="b5f91-121">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b5f91-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="b5f91-122">Les algorithmes de chiffrement utilisés par l’application ne doivent pas nécessairement être conformes à la norme FIPS, quelle que soit la configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b5f91-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5f91-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b5f91-123">Child Elements</span></span>  
 <span data-ttu-id="b5f91-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b5f91-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5f91-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b5f91-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b5f91-126">Élément</span><span class="sxs-lookup"><span data-stu-id="b5f91-126">Element</span></span>|<span data-ttu-id="b5f91-127">Description</span><span class="sxs-lookup"><span data-stu-id="b5f91-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b5f91-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5f91-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b5f91-129">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b5f91-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5f91-130">Notes</span><span class="sxs-lookup"><span data-stu-id="b5f91-130">Remarks</span></span>  
 <span data-ttu-id="b5f91-131">À partir de la .NET Framework 2,0, la création de classes qui implémentent des algorithmes de chiffrement est contrôlée par la configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b5f91-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="b5f91-132">Si l’ordinateur est configuré pour exiger la conformité des algorithmes avec FIPS et qu’une classe implémente un algorithme qui n’est pas compatible avec FIPS, toute tentative de création d’une instance de cette classe lève une exception.</span><span class="sxs-lookup"><span data-stu-id="b5f91-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="b5f91-133">Les constructeurs lèvent <xref:System.InvalidOperationException> une exception, `Create` et les méthodes <xref:System.Reflection.TargetInvocationException> lèvent une exception <xref:System.InvalidOperationException> avec une exception interne.</span><span class="sxs-lookup"><span data-stu-id="b5f91-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="b5f91-134">Si votre application s’exécute sur des ordinateurs dont les configurations nécessitent une compatibilité avec FIPS et que votre application utilise un algorithme qui n’est pas compatible avec FIPS, vous pouvez utiliser cet élément dans votre fichier de configuration pour empêcher le common language runtime (CLR) à partir de application de la conformité FIPS.</span><span class="sxs-lookup"><span data-stu-id="b5f91-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="b5f91-135">Cet élément a été introduit dans le .NET Framework 2,0 Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="b5f91-135">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5f91-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5f91-136">Example</span></span>  
 <span data-ttu-id="b5f91-137">L’exemple suivant montre comment empêcher le CLR d’appliquer la conformité FIPS.</span><span class="sxs-lookup"><span data-stu-id="b5f91-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5f91-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5f91-138">See also</span></span>

- [<span data-ttu-id="b5f91-139">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="b5f91-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b5f91-140">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b5f91-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b5f91-141">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="b5f91-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)
