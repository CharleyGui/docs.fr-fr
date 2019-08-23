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
ms.openlocfilehash: 5ba781598542d271f41476b1a1e9d61faeb6ff74
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927181"
---
# <a name="assert-element"></a><span data-ttu-id="e4b53-102">\<Élément > Assert</span><span class="sxs-lookup"><span data-stu-id="e4b53-102">\<assert> Element</span></span>
<span data-ttu-id="e4b53-103">Indique si une boîte de message doit s’afficher quand vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; spécifie également le nom du fichier dans lequel écrire les messages.</span><span class="sxs-lookup"><span data-stu-id="e4b53-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="e4b53-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e4b53-104">\<configuration></span></span>  
<span data-ttu-id="e4b53-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="e4b53-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e4b53-106">\<assert></span><span class="sxs-lookup"><span data-stu-id="e4b53-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4b53-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4b53-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4b53-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e4b53-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e4b53-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e4b53-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4b53-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e4b53-110">Attributes</span></span>  
  
|<span data-ttu-id="e4b53-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="e4b53-111">Attribute</span></span>|<span data-ttu-id="e4b53-112">Description</span><span class="sxs-lookup"><span data-stu-id="e4b53-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="e4b53-113">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e4b53-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e4b53-114">Spécifie s’il faut afficher une boîte de message lorsque la méthode **Debug. Assert** prend la **valeur false**.</span><span class="sxs-lookup"><span data-stu-id="e4b53-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="e4b53-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e4b53-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e4b53-116">Spécifie le nom du fichier dans lequel le message doit être écrit si **Debug. Assert** prend la **valeur false**.</span><span class="sxs-lookup"><span data-stu-id="e4b53-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="e4b53-117">Attribut AssertUiEnabled</span><span class="sxs-lookup"><span data-stu-id="e4b53-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="e4b53-118">`Value`</span><span class="sxs-lookup"><span data-stu-id="e4b53-118">Value</span></span>|<span data-ttu-id="e4b53-119">Description</span><span class="sxs-lookup"><span data-stu-id="e4b53-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="e4b53-120">Affiche la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="e4b53-120">Displays the message box.</span></span> <span data-ttu-id="e4b53-121">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4b53-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="e4b53-122">N’affiche pas la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="e4b53-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4b53-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e4b53-123">Child Elements</span></span>  
 <span data-ttu-id="e4b53-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e4b53-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4b53-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e4b53-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e4b53-126">Élément</span><span class="sxs-lookup"><span data-stu-id="e4b53-126">Element</span></span>|<span data-ttu-id="e4b53-127">Description</span><span class="sxs-lookup"><span data-stu-id="e4b53-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e4b53-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4b53-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e4b53-129">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="e4b53-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4b53-130">Notes</span><span class="sxs-lookup"><span data-stu-id="e4b53-130">Remarks</span></span>  
 <span data-ttu-id="e4b53-131">Les deux attributs de  **\<** l’élément Assert > sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="e4b53-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="e4b53-132">Vous pouvez désactiver les boîtes de message sans spécifier de fichier dans lequel écrire les messages, ou vous pouvez spécifier un fichier dans lequel écrire les messages tout en laissant les boîtes de message activées.</span><span class="sxs-lookup"><span data-stu-id="e4b53-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4b53-133">Exemples</span><span class="sxs-lookup"><span data-stu-id="e4b53-133">Example</span></span>  
 <span data-ttu-id="e4b53-134">L’exemple suivant montre comment désactiver l’affichage des boîtes de message lorsque vous appelez **Debug. Assert** et écrire `c:\log.txt`les messages dans.</span><span class="sxs-lookup"><span data-stu-id="e4b53-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4b53-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4b53-135">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="e4b53-136">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="e4b53-136">Trace and Debug Settings Schema</span></span>](index.md)
