---
title: élément <add> pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215434"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="35234-102">\<ajouter un élément > pour NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="35234-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="35234-103">Ajoute des paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="35234-103">Adds custom application settings.</span></span> <span data-ttu-id="35234-104">Chaque **\<ajouter >** balise contient une paire clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="35234-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="35234-105">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="35234-105">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="35234-106">&nbsp;&nbsp;[ **\<** ](custom-element-2.md) de la\ >.</span><span class="sxs-lookup"><span data-stu-id="35234-106">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\</span></span>
<span data-ttu-id="35234-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<ajouter des >**</span><span class="sxs-lookup"><span data-stu-id="35234-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="35234-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35234-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="35234-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="35234-109">Attributes</span></span>

| <span data-ttu-id="35234-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="35234-110">Attribute</span></span> | <span data-ttu-id="35234-111">Description</span><span class="sxs-lookup"><span data-stu-id="35234-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="35234-112">**key**</span><span class="sxs-lookup"><span data-stu-id="35234-112">**key**</span></span>   | <span data-ttu-id="35234-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="35234-113">Required attribute.</span></span><br><br><span data-ttu-id="35234-114">Spécifie le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="35234-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="35234-115">**value**</span><span class="sxs-lookup"><span data-stu-id="35234-115">**value**</span></span> | <span data-ttu-id="35234-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="35234-116">Required attribute.</span></span><br><br><span data-ttu-id="35234-117">Spécifie la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="35234-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="35234-118">Élément parent</span><span class="sxs-lookup"><span data-stu-id="35234-118">Parent element</span></span>

| <span data-ttu-id="35234-119">Élément</span><span class="sxs-lookup"><span data-stu-id="35234-119">Element</span></span> | <span data-ttu-id="35234-120">Description</span><span class="sxs-lookup"><span data-stu-id="35234-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="35234-121"> **\<** de la > Appartient</span><span class="sxs-lookup"><span data-stu-id="35234-121">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="35234-122">Définit les paramètres des sections de configuration personnalisées qui utilisent les classes <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="35234-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="35234-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="35234-123">Child elements</span></span>

<span data-ttu-id="35234-124">None</span><span class="sxs-lookup"><span data-stu-id="35234-124">None</span></span>

## <a name="example"></a><span data-ttu-id="35234-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="35234-125">Example</span></span>

<span data-ttu-id="35234-126">L’exemple suivant montre comment définir une section de configuration personnalisée et utiliser l’élément **\<ajouter >** pour placer des paramètres dans la section :</span><span class="sxs-lookup"><span data-stu-id="35234-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="35234-127">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="35234-127">Configuration file</span></span>

<span data-ttu-id="35234-128">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="35234-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="35234-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35234-129">See also</span></span>

- [<span data-ttu-id="35234-130">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="35234-130">Configuration file schema for the .NET Framework</span></span>](index.md)
