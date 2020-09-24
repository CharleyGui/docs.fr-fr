---
title: Élément <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: c0dc190e69ca9650d518ee297b12f79f8c47d58b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183973"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="55f18-102">Élément \<shadowCopyVerifyByTimestamp></span><span class="sxs-lookup"><span data-stu-id="55f18-102">\<shadowCopyVerifyByTimestamp> Element</span></span>

<span data-ttu-id="55f18-103">Spécifie si les clichés instantanés utilisent le comportement de démarrage par défaut introduit dans le .NET Framework 4, ou repassent au comportement de démarrage des versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55f18-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a><span data-ttu-id="55f18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55f18-104">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55f18-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="55f18-105">Attributes and Elements</span></span>  

 <span data-ttu-id="55f18-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="55f18-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55f18-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="55f18-107">Attributes</span></span>  
  
|<span data-ttu-id="55f18-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="55f18-108">Attribute</span></span>|<span data-ttu-id="55f18-109">Description</span><span class="sxs-lookup"><span data-stu-id="55f18-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55f18-110">enabled</span><span class="sxs-lookup"><span data-stu-id="55f18-110">enabled</span></span>|<span data-ttu-id="55f18-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="55f18-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="55f18-112">Spécifie si les domaines d’application qui utilisent des clichés instantanés comparent les horodatages de l’assembly au démarrage, afin de déterminer si un assembly a été mis à jour avant de copier l’assembly.</span><span class="sxs-lookup"><span data-stu-id="55f18-112">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="55f18-113">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="55f18-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="55f18-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="55f18-114">Value</span></span>|<span data-ttu-id="55f18-115">Description</span><span class="sxs-lookup"><span data-stu-id="55f18-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="55f18-116">true</span><span class="sxs-lookup"><span data-stu-id="55f18-116">true</span></span>|<span data-ttu-id="55f18-117">Au démarrage, copie uniquement les assemblys qui ont été mis à jour depuis leur dernière copie dans le répertoire des clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="55f18-117">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="55f18-118">Il s’agit de la valeur par défaut pour le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55f18-118">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="55f18-119">false</span><span class="sxs-lookup"><span data-stu-id="55f18-119">false</span></span>|<span data-ttu-id="55f18-120">Rétablit le comportement de démarrage des versions précédentes du .NET Framework, qui consistait à copier tous les fichiers au démarrage.</span><span class="sxs-lookup"><span data-stu-id="55f18-120">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55f18-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="55f18-121">Child Elements</span></span>  

 <span data-ttu-id="55f18-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="55f18-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55f18-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="55f18-123">Parent Elements</span></span>  
  
|<span data-ttu-id="55f18-124">Élément</span><span class="sxs-lookup"><span data-stu-id="55f18-124">Element</span></span>|<span data-ttu-id="55f18-125">Description</span><span class="sxs-lookup"><span data-stu-id="55f18-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55f18-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55f18-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="55f18-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="55f18-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55f18-128">Notes</span><span class="sxs-lookup"><span data-stu-id="55f18-128">Remarks</span></span>  

 <span data-ttu-id="55f18-129">À partir du .NET Framework 4, les assemblys sont des clichés instantanés uniquement si leurs horodatages indiquent qu’ils ont été modifiés depuis leur dernière copie dans le répertoire des clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="55f18-129">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="55f18-130">Cela permet d’améliorer les temps de démarrage de nombreuses applications qui utilisent des clichés instantanés, comme décrit dans [clichés instantanés d’assemblys](../../../app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="55f18-130">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="55f18-131">Les applications qui ont un pourcentage élevé et la fréquence des mises à jour d’assembly peuvent ne pas tirer parti de ce changement de comportement.</span><span class="sxs-lookup"><span data-stu-id="55f18-131">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="55f18-132">Dans ce cas, vous pouvez utiliser cet élément pour restaurer le comportement des versions précédentes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55f18-132">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55f18-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="55f18-133">Example</span></span>  

 <span data-ttu-id="55f18-134">L’exemple suivant montre comment désactiver le comportement de démarrage par défaut des clichés instantanés dans le .NET Framework 4 et rétablir le comportement de démarrage des versions précédentes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55f18-134">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55f18-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55f18-135">See also</span></span>

- [<span data-ttu-id="55f18-136">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="55f18-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="55f18-137">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="55f18-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="55f18-138">Clichés instantanés d'assemblys</span><span class="sxs-lookup"><span data-stu-id="55f18-138">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
