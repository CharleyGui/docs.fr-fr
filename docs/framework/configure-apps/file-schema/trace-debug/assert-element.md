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
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088944"
---
# <a name="assert-element"></a><span data-ttu-id="50943-102">\<déclarer > élément</span><span class="sxs-lookup"><span data-stu-id="50943-102">\<assert> Element</span></span>
<span data-ttu-id="50943-103">Indique si une boîte de message doit s’afficher quand vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; spécifie également le nom du fichier dans lequel écrire les messages.</span><span class="sxs-lookup"><span data-stu-id="50943-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

<span data-ttu-id="50943-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="50943-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="50943-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="50943-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="50943-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Assert >**</span><span class="sxs-lookup"><span data-stu-id="50943-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**</span></span>

## <a name="syntax"></a><span data-ttu-id="50943-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50943-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50943-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="50943-108">Attributes and Elements</span></span>  
 <span data-ttu-id="50943-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="50943-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50943-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="50943-110">Attributes</span></span>  
  
|<span data-ttu-id="50943-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="50943-111">Attribute</span></span>|<span data-ttu-id="50943-112">Description</span><span class="sxs-lookup"><span data-stu-id="50943-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="50943-113">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="50943-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="50943-114">Spécifie s’il faut afficher une boîte de message lorsque la méthode **Debug. Assert** prend la **valeur false**.</span><span class="sxs-lookup"><span data-stu-id="50943-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="50943-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="50943-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="50943-116">Spécifie le nom du fichier dans lequel le message doit être écrit si **Debug. Assert** prend la **valeur false**.</span><span class="sxs-lookup"><span data-stu-id="50943-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="50943-117">Attribut AssertUiEnabled</span><span class="sxs-lookup"><span data-stu-id="50943-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="50943-118">valeur</span><span class="sxs-lookup"><span data-stu-id="50943-118">Value</span></span>|<span data-ttu-id="50943-119">Description</span><span class="sxs-lookup"><span data-stu-id="50943-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="50943-120">Affiche la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="50943-120">Displays the message box.</span></span> <span data-ttu-id="50943-121">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="50943-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="50943-122">N’affiche pas la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="50943-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50943-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="50943-123">Child Elements</span></span>  
 <span data-ttu-id="50943-124">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="50943-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50943-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="50943-125">Parent Elements</span></span>  
  
|<span data-ttu-id="50943-126">Élément</span><span class="sxs-lookup"><span data-stu-id="50943-126">Element</span></span>|<span data-ttu-id="50943-127">Description</span><span class="sxs-lookup"><span data-stu-id="50943-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="50943-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50943-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="50943-129">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="50943-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50943-130">Notes</span><span class="sxs-lookup"><span data-stu-id="50943-130">Remarks</span></span>  
 <span data-ttu-id="50943-131">Les deux attributs de l’élément **\<Assert >** sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="50943-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="50943-132">Vous pouvez désactiver les boîtes de message sans spécifier de fichier dans lequel écrire les messages, ou vous pouvez spécifier un fichier dans lequel écrire les messages tout en laissant les boîtes de message activées.</span><span class="sxs-lookup"><span data-stu-id="50943-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50943-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="50943-133">Example</span></span>  
 <span data-ttu-id="50943-134">L’exemple suivant montre comment désactiver l’affichage des boîtes de message lorsque vous appelez **Debug. Assert** et écrire les messages dans `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="50943-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="50943-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50943-135">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="50943-136">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="50943-136">Trace and Debug Settings Schema</span></span>](index.md)
