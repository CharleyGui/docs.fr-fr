---
title: Élément <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: 864a371d4ad10585e672452ad85cc09d4b684068
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158836"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="e4a95-102">Élément \<enforceFIPSPolicy></span><span class="sxs-lookup"><span data-stu-id="e4a95-102">\<enforceFIPSPolicy> Element</span></span>

<span data-ttu-id="e4a95-103">Indique s’il faut appliquer la condition de configuration d’ordinateur selon laquelle les algorithmes de chiffrement doivent être conformes aux normes FIPS (Federal Information Processing Standard).</span><span class="sxs-lookup"><span data-stu-id="e4a95-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="e4a95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4a95-104">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4a95-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e4a95-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e4a95-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e4a95-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4a95-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="e4a95-107">Attributes</span></span>  
  
|<span data-ttu-id="e4a95-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="e4a95-108">Attribute</span></span>|<span data-ttu-id="e4a95-109">Description</span><span class="sxs-lookup"><span data-stu-id="e4a95-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4a95-110">enabled</span><span class="sxs-lookup"><span data-stu-id="e4a95-110">enabled</span></span>|<span data-ttu-id="e4a95-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="e4a95-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="e4a95-112">Spécifie s’il faut activer la mise en application d’une exigence de configuration d’ordinateur que les algorithmes de chiffrement doivent être conformes à la norme FIPS.</span><span class="sxs-lookup"><span data-stu-id="e4a95-112">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e4a95-113">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="e4a95-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="e4a95-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="e4a95-114">Value</span></span>|<span data-ttu-id="e4a95-115">Description</span><span class="sxs-lookup"><span data-stu-id="e4a95-115">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="e4a95-116">Si votre ordinateur est configuré pour exiger que les algorithmes de chiffrement soient compatibles FIPS, cette exigence est appliquée.</span><span class="sxs-lookup"><span data-stu-id="e4a95-116">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="e4a95-117">Si une classe implémente un algorithme qui n’est pas compatible avec FIPS, les constructeurs ou les `Create` méthodes de cette classe lèvent des exceptions lorsqu’elles sont exécutées sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e4a95-117">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="e4a95-118">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4a95-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="e4a95-119">Les algorithmes de chiffrement utilisés par l’application ne doivent pas nécessairement être conformes à la norme FIPS, quelle que soit la configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e4a95-119">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4a95-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e4a95-120">Child Elements</span></span>  

 <span data-ttu-id="e4a95-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e4a95-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4a95-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e4a95-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e4a95-123">Élément</span><span class="sxs-lookup"><span data-stu-id="e4a95-123">Element</span></span>|<span data-ttu-id="e4a95-124">Description</span><span class="sxs-lookup"><span data-stu-id="e4a95-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e4a95-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4a95-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e4a95-126">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e4a95-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4a95-127">Notes</span><span class="sxs-lookup"><span data-stu-id="e4a95-127">Remarks</span></span>  

 <span data-ttu-id="e4a95-128">À partir de la .NET Framework 2,0, la création de classes qui implémentent des algorithmes de chiffrement est contrôlée par la configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e4a95-128">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="e4a95-129">Si l’ordinateur est configuré pour exiger la conformité des algorithmes avec FIPS et qu’une classe implémente un algorithme qui n’est pas compatible avec FIPS, toute tentative de création d’une instance de cette classe lève une exception.</span><span class="sxs-lookup"><span data-stu-id="e4a95-129">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="e4a95-130">Les constructeurs lèvent une <xref:System.InvalidOperationException> exception, et les `Create` méthodes lèvent une <xref:System.Reflection.TargetInvocationException> exception avec une <xref:System.InvalidOperationException> exception interne.</span><span class="sxs-lookup"><span data-stu-id="e4a95-130">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="e4a95-131">Si votre application s’exécute sur des ordinateurs dont les configurations nécessitent une compatibilité avec FIPS et que votre application utilise un algorithme qui n’est pas compatible avec FIPS, vous pouvez utiliser cet élément dans votre fichier de configuration pour empêcher le common language runtime (CLR) d’appliquer la conformité FIPS.</span><span class="sxs-lookup"><span data-stu-id="e4a95-131">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="e4a95-132">Cet élément a été introduit dans le .NET Framework 2,0 Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="e4a95-132">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4a95-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="e4a95-133">Example</span></span>  

 <span data-ttu-id="e4a95-134">L’exemple suivant montre comment empêcher le CLR d’appliquer la conformité FIPS.</span><span class="sxs-lookup"><span data-stu-id="e4a95-134">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4a95-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4a95-135">See also</span></span>

- [<span data-ttu-id="e4a95-136">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="e4a95-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e4a95-137">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="e4a95-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e4a95-138">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="e4a95-138">Cryptography Model</span></span>](../../../../standard/security/cryptography-model.md)
