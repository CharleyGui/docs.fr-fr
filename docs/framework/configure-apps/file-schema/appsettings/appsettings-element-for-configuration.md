---
title: <appSettings>, élément de <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155529"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="b8b88-102">\<appSettings>, élément de \<configuration></span><span class="sxs-lookup"><span data-stu-id="b8b88-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="b8b88-103">Contient des paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="b8b88-103">Contains custom application settings.</span></span> <span data-ttu-id="b8b88-104">Il s’agit d’une section de configuration prédéfinie fournie par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8b88-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="b8b88-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="b8b88-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b8b88-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8b88-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="b8b88-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="b8b88-107">Attribute</span></span>

|           | <span data-ttu-id="b8b88-108">Description</span><span class="sxs-lookup"><span data-stu-id="b8b88-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="b8b88-109">**txt**</span><span class="sxs-lookup"><span data-stu-id="b8b88-109">**file**</span></span>  | <span data-ttu-id="b8b88-110">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="b8b88-110">Optional attribute.</span></span><br><br><span data-ttu-id="b8b88-111">Spécifie un chemin d’accès relatif à un fichier externe contenant les paramètres de configuration d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="b8b88-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="b8b88-112">Le fichier spécifié contient le même type de paramètres que ceux spécifiés dans **\<add>** les **\<remove>** éléments, et **\<clear>** et utilise le même format de paire clé/valeur que ces éléments.</span><span class="sxs-lookup"><span data-stu-id="b8b88-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="b8b88-113">Le chemin d’accès spécifié est relatif au fichier de configuration principal.</span><span class="sxs-lookup"><span data-stu-id="b8b88-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="b8b88-114">Pour une application Windows Forms, il s’agit du dossier binaire (tel que */bin/debug*), et non de l’emplacement du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="b8b88-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="b8b88-115">Pour les applications Web Forms, le chemin d’accès est relatif à la racine de l’application, où se trouve le fichier *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="b8b88-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="b8b88-116">Le runtime ignore l’attribut si le fichier spécifié est introuvable.</span><span class="sxs-lookup"><span data-stu-id="b8b88-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="b8b88-117">Élément parent</span><span class="sxs-lookup"><span data-stu-id="b8b88-117">Parent element</span></span>

|     | <span data-ttu-id="b8b88-118">Description</span><span class="sxs-lookup"><span data-stu-id="b8b88-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b8b88-119">**\<configuration>** Appartient</span><span class="sxs-lookup"><span data-stu-id="b8b88-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="b8b88-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8b88-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b8b88-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b8b88-121">Child elements</span></span>

|     | <span data-ttu-id="b8b88-122">Description</span><span class="sxs-lookup"><span data-stu-id="b8b88-122">Description</span></span> |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="b8b88-123">Ajoute un paramètre d’application personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b8b88-123">Adds a custom application setting.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="b8b88-124">Efface tous les paramètres d’application précédemment définis.</span><span class="sxs-lookup"><span data-stu-id="b8b88-124">Clears all previously defined application settings.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="b8b88-125">Supprime un paramètre d’application défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="b8b88-125">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="b8b88-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="b8b88-126">Remarks</span></span>

<span data-ttu-id="b8b88-127">L' **\<appSettings>** élément stocke des informations de configuration d’application personnalisées, telles que des chaînes de connexion de base de données, des chemins de fichier, des URL de service Web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="b8b88-127">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="b8b88-128">Les paires clé/valeur spécifiées dans l' **\<appSettings>** élément sont accessibles dans le code à l’aide de la <xref:System.Configuration.ConfigurationSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="b8b88-128">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="b8b88-129">Vous pouvez utiliser l’attribut **file** dans l' **\<appSettings>** élément des fichiers *Web. config* et de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="b8b88-129">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="b8b88-130">Cet attribut spécifie un fichier de configuration qui fournit des paramètres supplémentaires ou substitue les paramètres spécifiés dans l' **\<appSettings>** élément.</span><span class="sxs-lookup"><span data-stu-id="b8b88-130">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="b8b88-131">L’attribut de **fichier** peut être utilisé dans les scénarios de développement de l’équipe de contrôle de code source, par exemple lorsqu’un utilisateur souhaite remplacer les paramètres de projet spécifiés dans un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="b8b88-131">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="b8b88-132">Les fichiers de configuration spécifiés par l’attribut **file** doivent avoir un nœud racine **\<appSettings>** plutôt que **\<configuration>** .</span><span class="sxs-lookup"><span data-stu-id="b8b88-132">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="b8b88-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8b88-133">Example</span></span>

<span data-ttu-id="b8b88-134">L’exemple suivant montre un fichier de paramètres d’application externe (*custom.config*) qui définit un paramètre d’application personnalisé :</span><span class="sxs-lookup"><span data-stu-id="b8b88-134">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="b8b88-135">L’exemple suivant montre un fichier de configuration d’application qui consomme le paramètre dans le fichier de paramètres externes et définit un paramètre d’application qui lui est propre :</span><span class="sxs-lookup"><span data-stu-id="b8b88-135">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="b8b88-136">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="b8b88-136">Configuration file</span></span>

<span data-ttu-id="b8b88-137">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="b8b88-137">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8b88-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8b88-138">See also</span></span>

- [<span data-ttu-id="b8b88-139">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b8b88-139">Configuration file schema for the .NET Framework</span></span>](../index.md)
