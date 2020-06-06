---
title: Élément <assert>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: f3c1a1670139a8262dea449bfff99c7c1c19f088
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088944"
---
# <a name="assert-element"></a><span data-ttu-id="676ba-102">Élément \<assert></span><span class="sxs-lookup"><span data-stu-id="676ba-102">\<assert> Element</span></span>
<span data-ttu-id="676ba-103">Indique si une boîte de message doit s’afficher quand vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; spécifie également le nom du fichier dans lequel écrire les messages.</span><span class="sxs-lookup"><span data-stu-id="676ba-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**

## <a name="syntax"></a><span data-ttu-id="676ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="676ba-104">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="676ba-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="676ba-105">Attributes and Elements</span></span>  
 <span data-ttu-id="676ba-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="676ba-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="676ba-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="676ba-107">Attributes</span></span>  
  
|<span data-ttu-id="676ba-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="676ba-108">Attribute</span></span>|<span data-ttu-id="676ba-109">Description</span><span class="sxs-lookup"><span data-stu-id="676ba-109">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="676ba-110">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="676ba-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="676ba-111">Spécifie s’il faut afficher une boîte de message lorsque la méthode **Debug. Assert** prend la **valeur false**.</span><span class="sxs-lookup"><span data-stu-id="676ba-111">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="676ba-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="676ba-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="676ba-113">Spécifie le nom du fichier dans lequel le message doit être écrit si **Debug. Assert** prend la **valeur false**.</span><span class="sxs-lookup"><span data-stu-id="676ba-113">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="676ba-114">Attribut AssertUiEnabled</span><span class="sxs-lookup"><span data-stu-id="676ba-114">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="676ba-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="676ba-115">Value</span></span>|<span data-ttu-id="676ba-116">Description</span><span class="sxs-lookup"><span data-stu-id="676ba-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="676ba-117">Affiche la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="676ba-117">Displays the message box.</span></span> <span data-ttu-id="676ba-118">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="676ba-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="676ba-119">N’affiche pas la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="676ba-119">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="676ba-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="676ba-120">Child Elements</span></span>  
 <span data-ttu-id="676ba-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="676ba-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="676ba-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="676ba-122">Parent Elements</span></span>  
  
|<span data-ttu-id="676ba-123">Élément</span><span class="sxs-lookup"><span data-stu-id="676ba-123">Element</span></span>|<span data-ttu-id="676ba-124">Description</span><span class="sxs-lookup"><span data-stu-id="676ba-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="676ba-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="676ba-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="676ba-126">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="676ba-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="676ba-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="676ba-127">Remarks</span></span>  
 <span data-ttu-id="676ba-128">Les deux attributs de l' **\<assert>** élément sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="676ba-128">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="676ba-129">Vous pouvez désactiver les boîtes de message sans spécifier de fichier dans lequel écrire les messages, ou vous pouvez spécifier un fichier dans lequel écrire les messages tout en laissant les boîtes de message activées.</span><span class="sxs-lookup"><span data-stu-id="676ba-129">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="676ba-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="676ba-130">Example</span></span>  
 <span data-ttu-id="676ba-131">L’exemple suivant montre comment désactiver l’affichage des boîtes de message lorsque vous appelez **Debug. Assert** et écrire les messages dans `c:\log.txt` .</span><span class="sxs-lookup"><span data-stu-id="676ba-131">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="676ba-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="676ba-132">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="676ba-133">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="676ba-133">Trace and Debug Settings Schema</span></span>](index.md)
