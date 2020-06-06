---
title: <section> element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153726"
---
# <a name="section-element"></a><span data-ttu-id="064f5-102">\<section>, élément</span><span class="sxs-lookup"><span data-stu-id="064f5-102">\<section> element</span></span>

<span data-ttu-id="064f5-103">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="064f5-103">Contains a configuration section declaration.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a><span data-ttu-id="064f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="064f5-104">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="064f5-105">Attributs requis</span><span class="sxs-lookup"><span data-stu-id="064f5-105">Required attributes</span></span>

|           | <span data-ttu-id="064f5-106">Description</span><span class="sxs-lookup"><span data-stu-id="064f5-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="064f5-107">**name**</span><span class="sxs-lookup"><span data-stu-id="064f5-107">**name**</span></span>  | <span data-ttu-id="064f5-108">Spécifie le nom de la section de configuration.</span><span class="sxs-lookup"><span data-stu-id="064f5-108">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="064f5-109">**type**</span><span class="sxs-lookup"><span data-stu-id="064f5-109">**type**</span></span>  | <span data-ttu-id="064f5-110">Spécifie le nom de la classe de gestionnaire de section de configuration qui lit la section dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="064f5-110">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="064f5-111">La valeur de type a la syntaxe « Complete-Class-Handler-Class-Name, simple-assembly-name ».</span><span class="sxs-lookup"><span data-stu-id="064f5-111">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="064f5-112">Le nom d’assembly simple est le nom de fichier racine sans l’extension de fichier *. dll* .</span><span class="sxs-lookup"><span data-stu-id="064f5-112">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="064f5-113">Attributs facultatifs</span><span class="sxs-lookup"><span data-stu-id="064f5-113">Optional attributes</span></span>

<span data-ttu-id="064f5-114">Les attributs suivants s’appliquent uniquement aux applications ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="064f5-114">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="064f5-115">Le système de configuration ignore ces attributs pour d’autres types d’applications.</span><span class="sxs-lookup"><span data-stu-id="064f5-115">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="064f5-116">Description</span><span class="sxs-lookup"><span data-stu-id="064f5-116">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="064f5-117">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="064f5-117">**allowDefinition**</span></span> | <span data-ttu-id="064f5-118">Spécifie le fichier de configuration dans lequel la section peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="064f5-118">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="064f5-119">Utilisez l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="064f5-119">Use one of the following values:</span></span><br><br><span data-ttu-id="064f5-120">**Partout**</span><span class="sxs-lookup"><span data-stu-id="064f5-120">**Everywhere**</span></span><br><span data-ttu-id="064f5-121">Autorise l’utilisation de la section dans n’importe quel fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="064f5-121">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="064f5-122">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="064f5-122">This is the default.</span></span><br><span data-ttu-id="064f5-123">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="064f5-123">**MachineOnly**</span></span><br><span data-ttu-id="064f5-124">Autorise uniquement l’utilisation de la section dans le fichier de configuration de l’ordinateur (*machine. config*).</span><span class="sxs-lookup"><span data-stu-id="064f5-124">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="064f5-125">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="064f5-125">**MachineToApplication**</span></span><br><span data-ttu-id="064f5-126">Autorise l’utilisation de la section dans le fichier de configuration de l’ordinateur ou dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="064f5-126">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="064f5-127">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="064f5-127">**allowLocation**</span></span>   | <span data-ttu-id="064f5-128">Détermine si la section peut être utilisée dans l' **\<location>** élément.</span><span class="sxs-lookup"><span data-stu-id="064f5-128">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="064f5-129">Utilisez l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="064f5-129">Use one of the following values:</span></span><br><br><span data-ttu-id="064f5-130">**true**</span><span class="sxs-lookup"><span data-stu-id="064f5-130">**true**</span></span><br><span data-ttu-id="064f5-131">Autorise l’utilisation de la section dans l' **\<location>** élément.</span><span class="sxs-lookup"><span data-stu-id="064f5-131">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="064f5-132">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="064f5-132">This is the default.</span></span><br><span data-ttu-id="064f5-133">**false**</span><span class="sxs-lookup"><span data-stu-id="064f5-133">**false**</span></span><br><span data-ttu-id="064f5-134">N’autorise pas l’utilisation de la section dans l' **\<location>** élément.</span><span class="sxs-lookup"><span data-stu-id="064f5-134">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="064f5-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="064f5-135">Parent elements</span></span>

|     | <span data-ttu-id="064f5-136">Description</span><span class="sxs-lookup"><span data-stu-id="064f5-136">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="064f5-137">**\<configSections>** Appartient</span><span class="sxs-lookup"><span data-stu-id="064f5-137">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="064f5-138">Contient la section de configuration et les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="064f5-138">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="064f5-139">**\<sectionGroup>** Appartient</span><span class="sxs-lookup"><span data-stu-id="064f5-139">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="064f5-140">Définit un espace de noms pour les sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="064f5-140">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="064f5-141">Un **\<section>** élément est un élément enfant de **\<configSections>** ou, **\<sectionGroup>** mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="064f5-141">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="064f5-142">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="064f5-142">Child elements</span></span>

<span data-ttu-id="064f5-143">None</span><span class="sxs-lookup"><span data-stu-id="064f5-143">None</span></span>

## <a name="remarks"></a><span data-ttu-id="064f5-144">Notes</span><span class="sxs-lookup"><span data-stu-id="064f5-144">Remarks</span></span>

<span data-ttu-id="064f5-145">La déclaration d’une section de configuration définit essentiellement un nouvel élément pour le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="064f5-145">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="064f5-146">Le nouvel élément contient les paramètres qu’un gestionnaire de section de configuration (autrement dit, une classe qui implémente l' <xref:System.Configuration.IConfigurationSectionHandler> interface) lit.</span><span class="sxs-lookup"><span data-stu-id="064f5-146">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="064f5-147">Les attributs et les éléments enfants d’une section que vous définissez dépendent du gestionnaire de section que vous utilisez pour lire vos paramètres.</span><span class="sxs-lookup"><span data-stu-id="064f5-147">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="064f5-148">La déclaration d’un gestionnaire de section de configuration dans le fichier *machine. config* vous permet d’utiliser la section de configuration dans n’importe quel fichier de configuration d’application sur cet ordinateur, à moins que l’attribut **allowDefinition** spécifie autrement.</span><span class="sxs-lookup"><span data-stu-id="064f5-148">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="064f5-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="064f5-149">Example</span></span>

<span data-ttu-id="064f5-150">L’exemple suivant montre comment définir une section de configuration et définir les paramètres de cette section :</span><span class="sxs-lookup"><span data-stu-id="064f5-150">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler"
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="064f5-151">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="064f5-151">Configuration file</span></span>

<span data-ttu-id="064f5-152">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="064f5-152">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="064f5-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="064f5-153">See also</span></span>

- [<span data-ttu-id="064f5-154">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="064f5-154">Configuration file schema for the .NET Framework</span></span>](index.md)
