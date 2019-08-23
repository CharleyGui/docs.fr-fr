---
title: Élément personnalisé pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 890269857aaa00ce62195ccb2f4cb184b363b61e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921040"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="88af9-102">Élément personnalisé pour NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="88af9-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="88af9-103">Définit des paramètres pour les sections de configuration personnalisées <xref:System.Configuration.DictionarySectionHandler> qui utilisent les <xref:System.Configuration.NameValueSectionHandler> classes et.</span><span class="sxs-lookup"><span data-stu-id="88af9-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="88af9-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="88af9-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="88af9-105">&nbsp;&nbsp; **\<sectionName>**</span><span class="sxs-lookup"><span data-stu-id="88af9-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="88af9-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="88af9-106">Attributes</span></span>

<span data-ttu-id="88af9-107">Aucun</span><span class="sxs-lookup"><span data-stu-id="88af9-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="88af9-108">Élément parent</span><span class="sxs-lookup"><span data-stu-id="88af9-108">Parent element</span></span>

|     | <span data-ttu-id="88af9-109">Description</span><span class="sxs-lookup"><span data-stu-id="88af9-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="88af9-110"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="88af9-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="88af9-111">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="88af9-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="88af9-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="88af9-112">Child elements</span></span>

|     | <span data-ttu-id="88af9-113">Description</span><span class="sxs-lookup"><span data-stu-id="88af9-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="88af9-114">Ajouter > pour et [ **\<** ](add-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="88af9-114">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="88af9-115">Ajoute des paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="88af9-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="88af9-116">supprimer > pour et [ **\<** ](remove-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="88af9-116">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="88af9-117">Supprime un paramètre défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="88af9-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="88af9-118">désactivez <xref:System.Configuration.NameValueSectionHandler> > pour et [ **\<** ](clear-element-for-custom-2.md)<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="88af9-118">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="88af9-119">Efface tous les paramètres précédemment définis dans une section.</span><span class="sxs-lookup"><span data-stu-id="88af9-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="88af9-120">Notes</span><span class="sxs-lookup"><span data-stu-id="88af9-120">Remarks</span></span>

<span data-ttu-id="88af9-121">L'  **\<** élément de >y est un élément personnalisé défini par  **\<** une balise de > de section dans l'  **\<élément configSections >** .</span><span class="sxs-lookup"><span data-stu-id="88af9-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="88af9-122">Le tableau suivant indique le type d’objet retourné par la méthode ConfigurationSettings. GetConfig pour chaque gestionnaire de section de configuration:</span><span class="sxs-lookup"><span data-stu-id="88af9-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="88af9-123">Gestionnaire de section de configuration</span><span class="sxs-lookup"><span data-stu-id="88af9-123">Configuration section handler</span></span>                        | <span data-ttu-id="88af9-124">Type de retour</span><span class="sxs-lookup"><span data-stu-id="88af9-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="88af9-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="88af9-125">Example</span></span>

<span data-ttu-id="88af9-126">L’exemple suivant montre comment déclarer des sections qui utilisent les <xref:System.Configuration.DictionarySectionHandler> classes <xref:System.Configuration.NameValueSectionHandler> et.</span><span class="sxs-lookup"><span data-stu-id="88af9-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="88af9-127">Le premier élément personnalisé est  **\<dictionarySample >** , qui contient les paramètres lus par <xref:System.Configuration.DictionarySectionHandler> la classe dans `System.dll` l’assembly.</span><span class="sxs-lookup"><span data-stu-id="88af9-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="88af9-128">Le deuxième élément personnalisé est  **\<mySection >** , qui contient les paramètres lus par <xref:System.Configuration.NameValueSectionHandler> la classe dans `System.dll` l’assembly.</span><span class="sxs-lookup"><span data-stu-id="88af9-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="88af9-129">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="88af9-129">Configuration file</span></span>

<span data-ttu-id="88af9-130">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="88af9-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="88af9-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88af9-131">See also</span></span>

- [<span data-ttu-id="88af9-132">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="88af9-132">Configuration file schema for the .NET Framework</span></span>](index.md)
