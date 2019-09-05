---
title: < élément Crst_DisableSpinWait >
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a91e21120ecebbe7af2fb93798bc68d274fa92c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252713"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="9341a-102">\<Crst_DisableSpinWait >, élément</span><span class="sxs-lookup"><span data-stu-id="9341a-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="9341a-103">Spécifie s’il faut désactiver l’attente de spin pour une section critique en cas de conflit.</span><span class="sxs-lookup"><span data-stu-id="9341a-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
<span data-ttu-id="9341a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9341a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9341a-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="9341a-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="9341a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Crst_DisableSpinWait >**</span><span class="sxs-lookup"><span data-stu-id="9341a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9341a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9341a-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9341a-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9341a-108">Attributes and Elements</span></span>

<span data-ttu-id="9341a-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9341a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9341a-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="9341a-110">Attributes</span></span>  
  
|<span data-ttu-id="9341a-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="9341a-111">Attribute</span></span>|<span data-ttu-id="9341a-112">Description</span><span class="sxs-lookup"><span data-stu-id="9341a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9341a-113">**enabled**</span><span class="sxs-lookup"><span data-stu-id="9341a-113">**enabled**</span></span>|<span data-ttu-id="9341a-114">Spécifie si la rotation en attente des sections critiques lorsqu’elles sont confrontées est désactivée.</span><span class="sxs-lookup"><span data-stu-id="9341a-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9341a-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="9341a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="9341a-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="9341a-116">Value</span></span>|<span data-ttu-id="9341a-117">Description</span><span class="sxs-lookup"><span data-stu-id="9341a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9341a-118">1</span><span class="sxs-lookup"><span data-stu-id="9341a-118">1</span></span>|<span data-ttu-id="9341a-119">Désactivez l’attente de spin quand une section critique ne peut pas être acquise.</span><span class="sxs-lookup"><span data-stu-id="9341a-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="9341a-120">0</span><span class="sxs-lookup"><span data-stu-id="9341a-120">0</span></span>|<span data-ttu-id="9341a-121">Ne désactivez pas l’attente de spin quand une section critique ne peut pas être acquise.</span><span class="sxs-lookup"><span data-stu-id="9341a-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="9341a-122">Valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9341a-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9341a-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9341a-123">Child Elements</span></span>  
 <span data-ttu-id="9341a-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9341a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9341a-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9341a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9341a-126">Élément</span><span class="sxs-lookup"><span data-stu-id="9341a-126">Element</span></span>|<span data-ttu-id="9341a-127">Description</span><span class="sxs-lookup"><span data-stu-id="9341a-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9341a-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9341a-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9341a-129">Contient des informations sur les différents paramètres de configuration du Runtime.</span><span class="sxs-lookup"><span data-stu-id="9341a-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9341a-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="9341a-130">Example</span></span>  

<span data-ttu-id="9341a-131">L’exemple suivant désactive l’attente de spin-Wait dans les sections critiques en cas de conflit.</span><span class="sxs-lookup"><span data-stu-id="9341a-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9341a-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9341a-132">See also</span></span>

- [<span data-ttu-id="9341a-133">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="9341a-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9341a-134">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="9341a-134">Configuration File Schema</span></span>](../index.md)
