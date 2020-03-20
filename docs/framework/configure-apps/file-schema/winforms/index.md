---
title: Section de configuration de Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151830"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="07fba-102">Section de configuration de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="07fba-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="07fba-103">Les paramètres de configuration de Windows Forms permettent à une application Windows Forms de stocker et d’extraire des informations sur les paramètres d’application personnalisés, par exemple la prise en charge de plusieurs écrans, la prise en charge de la haute résolution et d’autres paramètres de configuration prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="07fba-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="07fba-104">Les paramètres de configuration de l’application Windows Forms sont stockés dans l’élément `System.Windows.Forms.ApplicationConfigurationSection` d’un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="07fba-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="07fba-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07fba-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07fba-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="07fba-106">Attributes and elements</span></span>

<span data-ttu-id="07fba-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="07fba-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="07fba-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="07fba-108">Attributes</span></span>

<span data-ttu-id="07fba-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="07fba-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07fba-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="07fba-110">Child elements</span></span>

<span data-ttu-id="07fba-111">Élément</span><span class="sxs-lookup"><span data-stu-id="07fba-111">Element</span></span>  |<span data-ttu-id="07fba-112">Description</span><span class="sxs-lookup"><span data-stu-id="07fba-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="07fba-113">Ajoute une clé de paramètre de configuration avec une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="07fba-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="07fba-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="07fba-114">Parent elements</span></span>

<span data-ttu-id="07fba-115">Élément</span><span class="sxs-lookup"><span data-stu-id="07fba-115">Element</span></span>  |<span data-ttu-id="07fba-116">Description</span><span class="sxs-lookup"><span data-stu-id="07fba-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="07fba-117">\<configuration></span><span class="sxs-lookup"><span data-stu-id="07fba-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="07fba-118">Élément racine de chaque fichier de configuration utilisé par le common language runtime et les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="07fba-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="07fba-119">Notes </span><span class="sxs-lookup"><span data-stu-id="07fba-119">Remarks</span></span>

<span data-ttu-id="07fba-120">À compter du .NET Framework 4.7, l’élément `<System.Windows.Forms.ApplicationConfigurationSection>` vous permet de configurer des applications Windows Forms pour tirer parti des fonctionnalités ajoutées dans les dernières versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07fba-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span>

<span data-ttu-id="07fba-121">L’élément `<System.Windows.Forms.ApplicationConfigurationSection>` peut inclure [`<add>`](windows-forms-add-configuration-element.md) un ou plusieurs éléments pour enfants, dont chacun définit un paramètre de configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="07fba-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="07fba-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07fba-122">See also</span></span>

- [<span data-ttu-id="07fba-123">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="07fba-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="07fba-124">Support DPI élevé dans les formulaires Windows</span><span class="sxs-lookup"><span data-stu-id="07fba-124">High DPI Support in Windows Forms</span></span>](../../../winforms/high-dpi-support-in-windows-forms.md)
