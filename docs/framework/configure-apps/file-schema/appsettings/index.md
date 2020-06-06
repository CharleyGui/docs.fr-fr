---
title: Schéma des paramètres d’application
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: 0a3363b35a6fc8bd27753eb034f8a1e95feb5292
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215430"
---
# <a name="app-settings-schema"></a><span data-ttu-id="606a6-102">Schéma des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="606a6-102">App Settings schema</span></span>

<span data-ttu-id="606a6-103">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="606a6-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| <span data-ttu-id="606a6-104">Élément</span><span class="sxs-lookup"><span data-stu-id="606a6-104">Element</span></span> | <span data-ttu-id="606a6-105">Description</span><span class="sxs-lookup"><span data-stu-id="606a6-105">Description</span></span> |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="606a6-106">Contient **\<add>** des **\<clear>** **\<remove>** balises, et pour contrôler les paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="606a6-106">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="606a6-107">A un attribut **file** facultatif.</span><span class="sxs-lookup"><span data-stu-id="606a6-107">Has an optional **file** attribute.</span></span> |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="606a6-108">Définit un paramètre.</span><span class="sxs-lookup"><span data-stu-id="606a6-108">Defines a setting.</span></span> <span data-ttu-id="606a6-109">Enfant de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="606a6-109">Child of **\<appSettings>**.</span></span> <span data-ttu-id="606a6-110">Requiert des attributs **key** et **value**.</span><span class="sxs-lookup"><span data-stu-id="606a6-110">Requires **key** and **value** attributes.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="606a6-111">Efface tous les paramètres.</span><span class="sxs-lookup"><span data-stu-id="606a6-111">Clears all settings.</span></span> <span data-ttu-id="606a6-112">Enfant de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="606a6-112">Child of **\<appSettings>**.</span></span> <span data-ttu-id="606a6-113">N’a pas d’attributs.</span><span class="sxs-lookup"><span data-stu-id="606a6-113">Has no attributes.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="606a6-114">Supprime un paramètre.</span><span class="sxs-lookup"><span data-stu-id="606a6-114">Removes a setting.</span></span> <span data-ttu-id="606a6-115">Enfant de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="606a6-115">Child of **\<appSettings>**.</span></span> <span data-ttu-id="606a6-116">Exige un attribut **key**.</span><span class="sxs-lookup"><span data-stu-id="606a6-116">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="606a6-117">\<appSettings>, élément</span><span class="sxs-lookup"><span data-stu-id="606a6-117">\<appSettings> element</span></span>

<span data-ttu-id="606a6-118">Cet élément contient **\<add>** des **\<clear>** **\<remove>** balises, et pour contrôler les paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="606a6-118">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="606a6-119">Il définit un attribut facultatif pour **file**.</span><span class="sxs-lookup"><span data-stu-id="606a6-119">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="606a6-120">\<add>, élément</span><span class="sxs-lookup"><span data-stu-id="606a6-120">\<add> element</span></span>

<span data-ttu-id="606a6-121">Ajoute un paramètre d’application personnalisé en tant que paire nom/valeur à la collection de paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="606a6-121">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="606a6-122">Il définit les attributs pour **key** et **value**.</span><span class="sxs-lookup"><span data-stu-id="606a6-122">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="606a6-123">\<clear>, élément</span><span class="sxs-lookup"><span data-stu-id="606a6-123">\<clear> element</span></span>

<span data-ttu-id="606a6-124">Supprime toutes les références aux paramètres d’application personnalisés hérités et autorise uniquement les références qui sont ajoutées par **\<add>** les éléments qui suivent l' **\<clear>** élément.</span><span class="sxs-lookup"><span data-stu-id="606a6-124">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="606a6-125">Il ne définit aucun attribut.</span><span class="sxs-lookup"><span data-stu-id="606a6-125">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="606a6-126">\<remove>, élément</span><span class="sxs-lookup"><span data-stu-id="606a6-126">\<remove> element</span></span>

<span data-ttu-id="606a6-127">Supprime une référence à un paramètre d’application personnalisé hérité de la collection de paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="606a6-127">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="606a6-128">Il définit un attribut pour **key**.</span><span class="sxs-lookup"><span data-stu-id="606a6-128">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="606a6-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="606a6-129">Example</span></span>

<span data-ttu-id="606a6-130">L’exemple suivant montre un fichier de paramètres d’application externe (*custom.config*) qui définit un paramètre d’application personnalisé :</span><span class="sxs-lookup"><span data-stu-id="606a6-130">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="606a6-131">L’exemple suivant montre un fichier de configuration d’application qui consomme le paramètre dans le fichier de paramètres externes et définit un paramètre d’application qui lui est propre :</span><span class="sxs-lookup"><span data-stu-id="606a6-131">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="606a6-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="606a6-132">See also</span></span>

- [<span data-ttu-id="606a6-133">Vue d’ensemble des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="606a6-133">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="606a6-134">Application Settings Architecture</span><span class="sxs-lookup"><span data-stu-id="606a6-134">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
