---
title: <assemblyBinding>, élément de <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155477"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="aad4c-102">\<assemblyBinding>, élément de \<configuration></span><span class="sxs-lookup"><span data-stu-id="aad4c-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="aad4c-103">Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.</span><span class="sxs-lookup"><span data-stu-id="aad4c-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="aad4c-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="aad4c-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="aad4c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aad4c-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="aad4c-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="aad4c-106">Attribute</span></span>

|           | <span data-ttu-id="aad4c-107">Description</span><span class="sxs-lookup"><span data-stu-id="aad4c-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="aad4c-108">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="aad4c-108">**xmlns**</span></span> | <span data-ttu-id="aad4c-109">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="aad4c-109">Required attribute.</span></span><br><br><span data-ttu-id="aad4c-110">Spécifie l'espace de noms XML requis pour la liaison d'assembly.</span><span class="sxs-lookup"><span data-stu-id="aad4c-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="aad4c-111">Utilisez la chaîne « urn:schemas-microsoft-com:asm.v1 » comme valeur.</span><span class="sxs-lookup"><span data-stu-id="aad4c-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="aad4c-112">Élément parent</span><span class="sxs-lookup"><span data-stu-id="aad4c-112">Parent element</span></span>

|     | <span data-ttu-id="aad4c-113">Description</span><span class="sxs-lookup"><span data-stu-id="aad4c-113">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="aad4c-114">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aad4c-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="aad4c-115">Élément enfant</span><span class="sxs-lookup"><span data-stu-id="aad4c-115">Child element</span></span>

|     | <span data-ttu-id="aad4c-116">Description</span><span class="sxs-lookup"><span data-stu-id="aad4c-116">Description</span></span> |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | <span data-ttu-id="aad4c-117">Spécifie un fichier de configuration à inclure.</span><span class="sxs-lookup"><span data-stu-id="aad4c-117">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="aad4c-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="aad4c-118">Remarks</span></span>

<span data-ttu-id="aad4c-119">L' [**\<linkedConfiguration>**](linkedconfiguration-element.md) élément simplifie la gestion des assemblys de composants en permettant aux fichiers de configuration de l’application d’inclure des fichiers de configuration d’assembly dans des emplacements bien connus, plutôt que de dupliquer des paramètres de configuration d’assembly.</span><span class="sxs-lookup"><span data-stu-id="aad4c-119">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="aad4c-120">L' **\<linkedConfiguration>** élément n’est pas pris en charge pour les applications avec des manifestes côte à côte Windows.</span><span class="sxs-lookup"><span data-stu-id="aad4c-120">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="aad4c-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="aad4c-121">Example</span></span>

<span data-ttu-id="aad4c-122">L’exemple suivant montre comment inclure un fichier de configuration sur le disque dur local :</span><span class="sxs-lookup"><span data-stu-id="aad4c-122">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="aad4c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aad4c-123">See also</span></span>

- [<span data-ttu-id="aad4c-124">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aad4c-124">Configuration file schema for the .NET Framework</span></span>](index.md)
