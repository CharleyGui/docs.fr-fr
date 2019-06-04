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
ms.openlocfilehash: 8636050b2618d1b2c2da0c08c756b0ed221c7f6f
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300760"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="2d69f-102">Élément personnalisé pour NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="2d69f-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="2d69f-103">Définit les paramètres pour les sections de configuration personnalisées qui utilisent le <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler> classes.</span><span class="sxs-lookup"><span data-stu-id="2d69f-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="2d69f-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)\\</span><span class="sxs-lookup"><span data-stu-id="2d69f-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)\\</span></span>
<span data-ttu-id="2d69f-105">&nbsp;&nbsp; **\<sectionName>**</span><span class="sxs-lookup"><span data-stu-id="2d69f-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="2d69f-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="2d69f-106">Attributes</span></span>

<span data-ttu-id="2d69f-107">None</span><span class="sxs-lookup"><span data-stu-id="2d69f-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="2d69f-108">Élément parent</span><span class="sxs-lookup"><span data-stu-id="2d69f-108">Parent element</span></span>

|     | <span data-ttu-id="2d69f-109">Description</span><span class="sxs-lookup"><span data-stu-id="2d69f-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2d69f-110"> *\*\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="2d69f-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="2d69f-111">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d69f-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="2d69f-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2d69f-112">Child elements</span></span>

|     | <span data-ttu-id="2d69f-113">Description</span><span class="sxs-lookup"><span data-stu-id="2d69f-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="2d69f-114">[ **\<Ajouter >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) pour <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="2d69f-114">[**\<add>**](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="2d69f-115">Ajoute des paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="2d69f-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="2d69f-116">[ **\<Supprimer >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) pour <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="2d69f-116">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="2d69f-117">Supprime un paramètre défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="2d69f-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="2d69f-118">[ **\<Désactivez >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) pour <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="2d69f-118">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="2d69f-119">Efface tous les paramètres déjà définis dans une section.</span><span class="sxs-lookup"><span data-stu-id="2d69f-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2d69f-120">Notes</span><span class="sxs-lookup"><span data-stu-id="2d69f-120">Remarks</span></span>

<span data-ttu-id="2d69f-121">Le  **\<sectionName >** est un élément personnalisé défini par un  **\<section >** balise dans le  **\<configSections >** élément.</span><span class="sxs-lookup"><span data-stu-id="2d69f-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="2d69f-122">Le tableau suivant présente que le type d’objet de la méthode ConfigurationSettings.GetConfig retourne pour chaque gestionnaire de section de configuration :</span><span class="sxs-lookup"><span data-stu-id="2d69f-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="2d69f-123">Gestionnaire de section de configuration</span><span class="sxs-lookup"><span data-stu-id="2d69f-123">Configuration section handler</span></span>                        | <span data-ttu-id="2d69f-124">Type de retour</span><span class="sxs-lookup"><span data-stu-id="2d69f-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="2d69f-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="2d69f-125">Example</span></span>

<span data-ttu-id="2d69f-126">L’exemple suivant montre comment déclarer les sections qui utilisent le <xref:System.Configuration.DictionarySectionHandler> et <xref:System.Configuration.NameValueSectionHandler> classes.</span><span class="sxs-lookup"><span data-stu-id="2d69f-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="2d69f-127">Le premier élément personnalisé est  **\<dictionarySample >** , qui contient les paramètres lus par le <xref:System.Configuration.DictionarySectionHandler> classe dans le `System.dll` assembly.</span><span class="sxs-lookup"><span data-stu-id="2d69f-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="2d69f-128">Le deuxième élément personnalisé est  **\<mySection >** , qui contient les paramètres lus par le <xref:System.Configuration.NameValueSectionHandler> classe dans le `System.dll` assembly.</span><span class="sxs-lookup"><span data-stu-id="2d69f-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="2d69f-129">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="2d69f-129">Configuration file</span></span>

<span data-ttu-id="2d69f-130">Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* fichiers qui ne sont pas au niveau du répertoire d’application.</span><span class="sxs-lookup"><span data-stu-id="2d69f-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d69f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d69f-131">See also</span></span>

- [<span data-ttu-id="2d69f-132">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2d69f-132">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
