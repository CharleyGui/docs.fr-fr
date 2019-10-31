---
title: Élément <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 160f14c856735e1ceac8635506aea52454faea43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115728"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="7730f-102">\<shadowCopyVerifyByTimestamp>, élément</span><span class="sxs-lookup"><span data-stu-id="7730f-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="7730f-103">Spécifie si les clichés instantanés utilisent le comportement de démarrage par défaut introduit dans le .NET Framework 4, ou repassent au comportement de démarrage des versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7730f-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
<span data-ttu-id="7730f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7730f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7730f-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="7730f-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="7730f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<shadowCopyVerifyByTimestamp** ></span><span class="sxs-lookup"><span data-stu-id="7730f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7730f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7730f-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7730f-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7730f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7730f-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7730f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7730f-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="7730f-110">Attributes</span></span>  
  
|<span data-ttu-id="7730f-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="7730f-111">Attribute</span></span>|<span data-ttu-id="7730f-112">Description</span><span class="sxs-lookup"><span data-stu-id="7730f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7730f-113">enabled</span><span class="sxs-lookup"><span data-stu-id="7730f-113">enabled</span></span>|<span data-ttu-id="7730f-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="7730f-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="7730f-115">Spécifie si les domaines d’application qui utilisent des clichés instantanés comparent les horodatages de l’assembly au démarrage, afin de déterminer si un assembly a été mis à jour avant de copier l’assembly.</span><span class="sxs-lookup"><span data-stu-id="7730f-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7730f-116">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="7730f-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="7730f-117">valeur</span><span class="sxs-lookup"><span data-stu-id="7730f-117">Value</span></span>|<span data-ttu-id="7730f-118">Description</span><span class="sxs-lookup"><span data-stu-id="7730f-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7730f-119">true</span><span class="sxs-lookup"><span data-stu-id="7730f-119">true</span></span>|<span data-ttu-id="7730f-120">Au démarrage, copie uniquement les assemblys qui ont été mis à jour depuis leur dernière copie dans le répertoire des clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="7730f-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="7730f-121">Il s’agit de la valeur par défaut pour le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7730f-121">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="7730f-122">False</span><span class="sxs-lookup"><span data-stu-id="7730f-122">false</span></span>|<span data-ttu-id="7730f-123">Rétablit le comportement de démarrage des versions précédentes du .NET Framework, qui consistait à copier tous les fichiers au démarrage.</span><span class="sxs-lookup"><span data-stu-id="7730f-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7730f-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7730f-124">Child Elements</span></span>  
 <span data-ttu-id="7730f-125">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="7730f-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7730f-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7730f-126">Parent Elements</span></span>  
  
|<span data-ttu-id="7730f-127">Élément</span><span class="sxs-lookup"><span data-stu-id="7730f-127">Element</span></span>|<span data-ttu-id="7730f-128">Description</span><span class="sxs-lookup"><span data-stu-id="7730f-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7730f-129">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7730f-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7730f-130">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7730f-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7730f-131">Notes</span><span class="sxs-lookup"><span data-stu-id="7730f-131">Remarks</span></span>  
 <span data-ttu-id="7730f-132">À partir du .NET Framework 4, les assemblys sont des clichés instantanés uniquement si leurs horodatages indiquent qu’ils ont été modifiés depuis leur dernière copie dans le répertoire des clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="7730f-132">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="7730f-133">Cela permet d’améliorer les temps de démarrage de nombreuses applications qui utilisent des clichés instantanés, comme décrit dans [clichés instantanés d’assemblys](../../../app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="7730f-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="7730f-134">Les applications qui ont un pourcentage élevé et la fréquence des mises à jour d’assembly peuvent ne pas tirer parti de ce changement de comportement.</span><span class="sxs-lookup"><span data-stu-id="7730f-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="7730f-135">Dans ce cas, vous pouvez utiliser cet élément pour restaurer le comportement des versions précédentes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7730f-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7730f-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="7730f-136">Example</span></span>  
 <span data-ttu-id="7730f-137">L’exemple suivant montre comment désactiver le comportement de démarrage par défaut des clichés instantanés dans le .NET Framework 4 et rétablir le comportement de démarrage des versions précédentes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7730f-137">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7730f-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7730f-138">See also</span></span>

- [<span data-ttu-id="7730f-139">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="7730f-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7730f-140">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="7730f-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7730f-141">Clichés instantanés d'assemblys</span><span class="sxs-lookup"><span data-stu-id="7730f-141">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
