---
title: Section de configuration de Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 8a6f13da9bf05d87c45d86a09261d0c7245f5b00
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546906"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="55717-102">Section de configuration de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="55717-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="55717-103">Les paramètres de configuration de Windows Forms permettent à une application Windows Forms de stocker et d’extraire des informations sur les paramètres d’application personnalisés, par exemple la prise en charge de plusieurs écrans, la prise en charge de la haute résolution et d’autres paramètres de configuration prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="55717-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="55717-104">Les paramètres de configuration de l’application Windows Forms sont stockés dans l’élément `System.Windows.Forms.ApplicationConfigurationSection` d’un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="55717-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="55717-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55717-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55717-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="55717-106">Attributes and elements</span></span>

<span data-ttu-id="55717-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="55717-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="55717-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="55717-108">Attributes</span></span>

<span data-ttu-id="55717-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="55717-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55717-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="55717-110">Child elements</span></span>

<span data-ttu-id="55717-111">Élément</span><span class="sxs-lookup"><span data-stu-id="55717-111">Element</span></span>  |<span data-ttu-id="55717-112">Description</span><span class="sxs-lookup"><span data-stu-id="55717-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="55717-113">Ajoute une clé de paramètre de configuration avec une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="55717-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="55717-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="55717-114">Parent elements</span></span>

<span data-ttu-id="55717-115">Élément</span><span class="sxs-lookup"><span data-stu-id="55717-115">Element</span></span>  |<span data-ttu-id="55717-116">Description</span><span class="sxs-lookup"><span data-stu-id="55717-116">Description</span></span> |
---------|---------|
[\<configuration>](../configuration-element.md) | <span data-ttu-id="55717-117">Élément racine de chaque fichier de configuration utilisé par le common language runtime et les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="55717-117">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="55717-118">Notes</span><span class="sxs-lookup"><span data-stu-id="55717-118">Remarks</span></span>

<span data-ttu-id="55717-119">À compter du .NET Framework 4.7, l’élément `<System.Windows.Forms.ApplicationConfigurationSection>` vous permet de configurer des applications Windows Forms pour tirer parti des fonctionnalités ajoutées dans les dernières versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55717-119">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span>

<span data-ttu-id="55717-120">L' `<System.Windows.Forms.ApplicationConfigurationSection>` élément peut inclure un ou plusieurs [`<add>`](windows-forms-add-configuration-element.md) éléments enfants, chacun d’eux définissant un paramètre de configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="55717-120">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="55717-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55717-121">See also</span></span>

- [<span data-ttu-id="55717-122">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="55717-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="55717-123">Prise en charge des résolutions élevées en Windows Forms</span><span class="sxs-lookup"><span data-stu-id="55717-123">High DPI Support in Windows Forms</span></span>](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)
