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
# <a name="assemblybinding-element-for-configuration"></a>\<assemblageBinding> élément pour \<la configuration>

Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.

configuration &nbsp; &nbsp;>[** \<**](configuration-element.md) ** \<assemblageBinding>**

## <a name="syntax"></a>Syntaxe

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **xmlns** | Attribut requis.<br><br>Spécifie l'espace de noms XML requis pour la liaison d'assembly. Utilisez la chaîne « urn:schemas-microsoft-com:asm.v1 » comme valeur. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-element"></a>Élément enfant

|     | Description |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | Spécifie un fichier de configuration à inclure. |

## <a name="remarks"></a>Notes 

[** \<L’élément linkedConfiguration>**](linkedconfiguration-element.md) simplifie la gestion des assemblages de composants en permettant aux fichiers de configuration d’application d’inclure des fichiers de configuration d’assemblage dans des endroits bien connus, plutôt que de dupliquer les paramètres de configuration d’assemblage.

> [!NOTE]
> ** \<L’élément linkedConfiguration>** n’est pas pris en charge pour les applications avec Windows côte à côte manifestes.

## <a name="example"></a> Exemple

L’exemple suivant montre comment inclure un fichier de configuration sur le disque dur local :

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le cadre .NET](index.md)
