---
title: Schéma paramètres d’application
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242827"
---
# <a name="application-settings-schema"></a><span data-ttu-id="c1503-102">Schéma paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="c1503-102">Application Settings schema</span></span>

<span data-ttu-id="c1503-103">Les paramètres d’application permettent à un formulaire Windows ou à une application ASP.NET de stocker et de récupérer les paramètres d’application et d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="c1503-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="c1503-104">Dans ce contexte, un *paramètre* est toute information spécifique à l’application ou spécifique à l’utilisateur actuel — n’importe quoi d’une chaîne de connexion de base de données à la taille de fenêtre par défaut préférée de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c1503-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="c1503-105">Par défaut, les paramètres d’application <xref:System.Configuration.LocalFileSettingsProvider> d’une application Windows Forms utilisent la classe, qui utilise le système de configuration .NET pour stocker les paramètres d’un fichier de configuration XML.</span><span class="sxs-lookup"><span data-stu-id="c1503-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="c1503-106">Pour plus d’informations sur les fichiers utilisés par les paramètres d’application, voir [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="c1503-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="c1503-107">Les paramètres d’application définissent les éléments suivants dans les fichiers de configuration qu’il utilise.</span><span class="sxs-lookup"><span data-stu-id="c1503-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="c1503-108">Élément</span><span class="sxs-lookup"><span data-stu-id="c1503-108">Element</span></span>                    | <span data-ttu-id="c1503-109">Description</span><span class="sxs-lookup"><span data-stu-id="c1503-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="c1503-110">**\<applicationSettings>**</span><span class="sxs-lookup"><span data-stu-id="c1503-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="c1503-111">Contient tous les \*\* \<réglages>\*\* des balises spécifiques à l’application.</span><span class="sxs-lookup"><span data-stu-id="c1503-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="c1503-112">**\<userSettings>**</span><span class="sxs-lookup"><span data-stu-id="c1503-112">**\<userSettings>**</span></span>        | <span data-ttu-id="c1503-113">Contient tous les \*\* \<réglages>\*\* des balises spécifiques à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="c1503-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="c1503-114">**\<>de réglage**</span><span class="sxs-lookup"><span data-stu-id="c1503-114">**\<setting>**</span></span>             | <span data-ttu-id="c1503-115">Définit un paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1503-115">Defines a setting.</span></span> <span data-ttu-id="c1503-116">Enfant \*\* \<d’applicationsSettings>\*\* ou \*\* \<userSettings>\*\*.</span><span class="sxs-lookup"><span data-stu-id="c1503-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="c1503-117">**\<>de valeur**</span><span class="sxs-lookup"><span data-stu-id="c1503-117">**\<value>**</span></span>               | <span data-ttu-id="c1503-118">Définit la valeur d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1503-118">Defines a setting's value.</span></span> <span data-ttu-id="c1503-119">Enfant \*\* \< \*\*de réglage>.</span><span class="sxs-lookup"><span data-stu-id="c1503-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="c1503-120">\<applicationSettings> élément</span><span class="sxs-lookup"><span data-stu-id="c1503-120">\<applicationSettings> element</span></span>

<span data-ttu-id="c1503-121">Cet élément contient tous les \*\* \<réglages>\*\* balises qui sont spécifiques à une instance de l’application sur un ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="c1503-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="c1503-122">Il ne définit aucun attribut.</span><span class="sxs-lookup"><span data-stu-id="c1503-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="c1503-123">\<userSettings> élément</span><span class="sxs-lookup"><span data-stu-id="c1503-123">\<userSettings> element</span></span>

<span data-ttu-id="c1503-124">Cet élément contient tous les \*\* \<réglages>\*\* balises qui sont spécifiques à l’utilisateur qui utilise actuellement l’application.</span><span class="sxs-lookup"><span data-stu-id="c1503-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="c1503-125">Il ne définit aucun attribut.</span><span class="sxs-lookup"><span data-stu-id="c1503-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="c1503-126">\<réglage> élément</span><span class="sxs-lookup"><span data-stu-id="c1503-126">\<setting> element</span></span>

<span data-ttu-id="c1503-127">Cet élément définit un paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1503-127">This element defines a setting.</span></span> <span data-ttu-id="c1503-128">Il a les attributs suivants.</span><span class="sxs-lookup"><span data-stu-id="c1503-128">It has the following attributes.</span></span>

| <span data-ttu-id="c1503-129">Attribut</span><span class="sxs-lookup"><span data-stu-id="c1503-129">Attribute</span></span>        | <span data-ttu-id="c1503-130">Description</span><span class="sxs-lookup"><span data-stu-id="c1503-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="c1503-131">**name**</span><span class="sxs-lookup"><span data-stu-id="c1503-131">**name**</span></span>         | <span data-ttu-id="c1503-132">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c1503-132">Required.</span></span> <span data-ttu-id="c1503-133">L’ID unique du réglage.</span><span class="sxs-lookup"><span data-stu-id="c1503-133">The unique ID of the setting.</span></span> <span data-ttu-id="c1503-134">Les paramètres créés par Visual `ProjectName.Properties.Settings`Studio sont enregistrés avec le nom .</span><span class="sxs-lookup"><span data-stu-id="c1503-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="c1503-135">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="c1503-135">**serializeAs**</span></span> | <span data-ttu-id="c1503-136">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c1503-136">Required.</span></span> <span data-ttu-id="c1503-137">Le format à utiliser pour sérialiser la valeur du texte.</span><span class="sxs-lookup"><span data-stu-id="c1503-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="c1503-138">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="c1503-138">Valid values are:</span></span><br><br><span data-ttu-id="c1503-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="c1503-139">- `string`.</span></span> <span data-ttu-id="c1503-140">La valeur est sérialisée <xref:System.ComponentModel.TypeConverter>comme une chaîne en utilisant un .</span><span class="sxs-lookup"><span data-stu-id="c1503-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="c1503-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="c1503-141">- `xml`.</span></span> <span data-ttu-id="c1503-142">La valeur est sérialisée à l’aide de la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="c1503-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="c1503-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="c1503-143">- `binary`.</span></span> <span data-ttu-id="c1503-144">La valeur est sérialisée sous forme binaire codé par texte à l’aide de la sérialisation binaire.</span><span class="sxs-lookup"><span data-stu-id="c1503-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="c1503-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="c1503-145">- `custom`.</span></span> <span data-ttu-id="c1503-146">Le fournisseur de paramètres a une connaissance inhérente de ce paramètre et sérialis et le détonalise.</span><span class="sxs-lookup"><span data-stu-id="c1503-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="c1503-147">\<valeur> élément</span><span class="sxs-lookup"><span data-stu-id="c1503-147">\<value> element</span></span>

<span data-ttu-id="c1503-148">Cet élément contient la valeur d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1503-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="c1503-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="c1503-149">Example</span></span>

<span data-ttu-id="c1503-150">L’exemple suivant montre un fichier de paramètres d’application qui définit deux paramètres d’application et deux paramètres à portée utilisateur :</span><span class="sxs-lookup"><span data-stu-id="c1503-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c1503-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1503-151">See also</span></span>

- [<span data-ttu-id="c1503-152">Vue d’ensemble des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="c1503-152">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="c1503-153">Application Settings Architecture</span><span class="sxs-lookup"><span data-stu-id="c1503-153">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
