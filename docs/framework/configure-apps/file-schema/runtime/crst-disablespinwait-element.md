---
title: Élément <Crst_DisableSpinWait>
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 45052d99bb297ac39d058fa405fe57a7c991f738
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151348"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="bc15a-102">\<Crst_DisableSpinWait> (élément)</span><span class="sxs-lookup"><span data-stu-id="bc15a-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="bc15a-103">Spécifie s’il faut désactiver l’attente de spin pour une section critique en cas de conflit.</span><span class="sxs-lookup"><span data-stu-id="bc15a-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="bc15a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc15a-104">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc15a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bc15a-105">Attributes and Elements</span></span>

<span data-ttu-id="bc15a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bc15a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc15a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="bc15a-107">Attributes</span></span>  
  
|<span data-ttu-id="bc15a-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="bc15a-108">Attribute</span></span>|<span data-ttu-id="bc15a-109">Description</span><span class="sxs-lookup"><span data-stu-id="bc15a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc15a-110">**activé**</span><span class="sxs-lookup"><span data-stu-id="bc15a-110">**enabled**</span></span>|<span data-ttu-id="bc15a-111">Spécifie si la rotation en attente des sections critiques lorsqu’elles sont confrontées est désactivée.</span><span class="sxs-lookup"><span data-stu-id="bc15a-111">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bc15a-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="bc15a-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="bc15a-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="bc15a-113">Value</span></span>|<span data-ttu-id="bc15a-114">Description</span><span class="sxs-lookup"><span data-stu-id="bc15a-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bc15a-115">1</span><span class="sxs-lookup"><span data-stu-id="bc15a-115">1</span></span>|<span data-ttu-id="bc15a-116">Désactivez l’attente de spin quand une section critique ne peut pas être acquise.</span><span class="sxs-lookup"><span data-stu-id="bc15a-116">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="bc15a-117">0</span><span class="sxs-lookup"><span data-stu-id="bc15a-117">0</span></span>|<span data-ttu-id="bc15a-118">Ne désactivez pas l’attente de spin quand une section critique ne peut pas être acquise.</span><span class="sxs-lookup"><span data-stu-id="bc15a-118">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="bc15a-119">Valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="bc15a-119">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc15a-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bc15a-120">Child Elements</span></span>  

 <span data-ttu-id="bc15a-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bc15a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc15a-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bc15a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="bc15a-123">Élément</span><span class="sxs-lookup"><span data-stu-id="bc15a-123">Element</span></span>|<span data-ttu-id="bc15a-124">Description</span><span class="sxs-lookup"><span data-stu-id="bc15a-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bc15a-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bc15a-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bc15a-126">Contient des informations sur les différents paramètres de configuration du Runtime.</span><span class="sxs-lookup"><span data-stu-id="bc15a-126">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bc15a-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc15a-127">Example</span></span>  

<span data-ttu-id="bc15a-128">L’exemple suivant désactive l’attente de spin-Wait dans les sections critiques en cas de conflit.</span><span class="sxs-lookup"><span data-stu-id="bc15a-128">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc15a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc15a-129">See also</span></span>

- [<span data-ttu-id="bc15a-130">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="bc15a-130">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bc15a-131">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="bc15a-131">Configuration File Schema</span></span>](../index.md)
