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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155477"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="1e528-102">\<assemblageBinding> élément pour \<la configuration></span><span class="sxs-lookup"><span data-stu-id="1e528-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="1e528-103">Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.</span><span class="sxs-lookup"><span data-stu-id="1e528-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="1e528-104">configuration &nbsp; &nbsp;>[\*\* \<\*\*](configuration-element.md) \*\* \<assemblageBinding>\*\*</span><span class="sxs-lookup"><span data-stu-id="1e528-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1e528-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e528-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="1e528-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="1e528-106">Attribute</span></span>

|           | <span data-ttu-id="1e528-107">Description</span><span class="sxs-lookup"><span data-stu-id="1e528-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="1e528-108">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="1e528-108">**xmlns**</span></span> | <span data-ttu-id="1e528-109">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="1e528-109">Required attribute.</span></span><br><br><span data-ttu-id="1e528-110">Spécifie l'espace de noms XML requis pour la liaison d'assembly.</span><span class="sxs-lookup"><span data-stu-id="1e528-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="1e528-111">Utilisez la chaîne « urn:schemas-microsoft-com:asm.v1 » comme valeur.</span><span class="sxs-lookup"><span data-stu-id="1e528-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="1e528-112">Élément parent</span><span class="sxs-lookup"><span data-stu-id="1e528-112">Parent element</span></span>

|     | <span data-ttu-id="1e528-113">Description</span><span class="sxs-lookup"><span data-stu-id="1e528-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1e528-114">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="1e528-114">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="1e528-115">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1e528-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="1e528-116">Élément enfant</span><span class="sxs-lookup"><span data-stu-id="1e528-116">Child element</span></span>

|     | <span data-ttu-id="1e528-117">Description</span><span class="sxs-lookup"><span data-stu-id="1e528-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1e528-118">**\<linkedConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="1e528-118">**\<linkedConfiguration>**</span></span>](linkedconfiguration-element.md) | <span data-ttu-id="1e528-119">Spécifie un fichier de configuration à inclure.</span><span class="sxs-lookup"><span data-stu-id="1e528-119">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="1e528-120">Notes </span><span class="sxs-lookup"><span data-stu-id="1e528-120">Remarks</span></span>

<span data-ttu-id="1e528-121">[\*\* \<L’élément linkedConfiguration>\*\*](linkedconfiguration-element.md) simplifie la gestion des assemblages de composants en permettant aux fichiers de configuration d’application d’inclure des fichiers de configuration d’assemblage dans des endroits bien connus, plutôt que de dupliquer les paramètres de configuration d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="1e528-121">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="1e528-122">\*\* \<L’élément linkedConfiguration>\*\* n’est pas pris en charge pour les applications avec Windows côte à côte manifestes.</span><span class="sxs-lookup"><span data-stu-id="1e528-122">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="1e528-123"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1e528-123">Example</span></span>

<span data-ttu-id="1e528-124">L’exemple suivant montre comment inclure un fichier de configuration sur le disque dur local :</span><span class="sxs-lookup"><span data-stu-id="1e528-124">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="1e528-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e528-125">See also</span></span>

- [<span data-ttu-id="1e528-126">Schéma de fichier de configuration pour le cadre .NET</span><span class="sxs-lookup"><span data-stu-id="1e528-126">Configuration file schema for the .NET Framework</span></span>](index.md)
