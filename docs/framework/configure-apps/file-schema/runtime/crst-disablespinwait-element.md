---
title: < élément Crst_DisableSpinWait >
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a52dd671f1fbf6fda5bdc92c0935784181eb4b03
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663839"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="e0d87-102">\<Crst_DisableSpinWait >, élément</span><span class="sxs-lookup"><span data-stu-id="e0d87-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="e0d87-103">Spécifie s’il faut désactiver l’attente de spin pour une section critique en cas de conflit.</span><span class="sxs-lookup"><span data-stu-id="e0d87-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
 <span data-ttu-id="e0d87-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e0d87-104">\<configuration></span></span>  
<span data-ttu-id="e0d87-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="e0d87-105">\<runtime></span></span>  
<span data-ttu-id="e0d87-106">\<Crst_DisableSpinWait></span><span class="sxs-lookup"><span data-stu-id="e0d87-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0d87-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0d87-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0d87-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e0d87-108">Attributes and Elements</span></span>

<span data-ttu-id="e0d87-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e0d87-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0d87-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e0d87-110">Attributes</span></span>  
  
|<span data-ttu-id="e0d87-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="e0d87-111">Attribute</span></span>|<span data-ttu-id="e0d87-112">Description</span><span class="sxs-lookup"><span data-stu-id="e0d87-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0d87-113">**enabled**</span><span class="sxs-lookup"><span data-stu-id="e0d87-113">**enabled**</span></span>|<span data-ttu-id="e0d87-114">Spécifie si la rotation en attente des sections critiques lorsqu’elles sont confrontées est désactivée.</span><span class="sxs-lookup"><span data-stu-id="e0d87-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e0d87-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="e0d87-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e0d87-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="e0d87-116">Value</span></span>|<span data-ttu-id="e0d87-117">Description</span><span class="sxs-lookup"><span data-stu-id="e0d87-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e0d87-118">1</span><span class="sxs-lookup"><span data-stu-id="e0d87-118">1</span></span>|<span data-ttu-id="e0d87-119">Désactivez l’attente de spin quand une section critique ne peut pas être acquise.</span><span class="sxs-lookup"><span data-stu-id="e0d87-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="e0d87-120">0</span><span class="sxs-lookup"><span data-stu-id="e0d87-120">0</span></span>|<span data-ttu-id="e0d87-121">Ne désactivez pas l’attente de spin quand une section critique ne peut pas être acquise.</span><span class="sxs-lookup"><span data-stu-id="e0d87-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="e0d87-122">Valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e0d87-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0d87-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e0d87-123">Child Elements</span></span>  
 <span data-ttu-id="e0d87-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e0d87-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0d87-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e0d87-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e0d87-126">Élément</span><span class="sxs-lookup"><span data-stu-id="e0d87-126">Element</span></span>|<span data-ttu-id="e0d87-127">Description</span><span class="sxs-lookup"><span data-stu-id="e0d87-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e0d87-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0d87-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e0d87-129">Contient des informations sur les différents paramètres de configuration du Runtime.</span><span class="sxs-lookup"><span data-stu-id="e0d87-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e0d87-130">Exemples</span><span class="sxs-lookup"><span data-stu-id="e0d87-130">Example</span></span>  

<span data-ttu-id="e0d87-131">L’exemple suivant désactive l’attente de spin-Wait dans les sections critiques en cas de conflit.</span><span class="sxs-lookup"><span data-stu-id="e0d87-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0d87-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0d87-132">See also</span></span>

- [<span data-ttu-id="e0d87-133">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="e0d87-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e0d87-134">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="e0d87-134">Configuration File Schema</span></span>](../index.md)
