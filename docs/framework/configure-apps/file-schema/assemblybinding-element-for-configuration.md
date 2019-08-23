---
title: <assemblyBinding>, élément de <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: e0b83c4b3573ab6819654e72cac1bf3e4a0ba637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921271"
---
# <a name="assemblybinding-element-for-configuration"></a>\<élément assemblyBinding > pour \<la configuration >

Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; **\<assemblyBinding>**

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
| [ **\<configuration>** ](configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-element"></a>Élément enfant

|     | Description |
| --- | ----------- |
| [ **\<linkedConfiguration>** ](linkedconfiguration-element.md) | Spécifie un fichier de configuration à inclure. |

## <a name="remarks"></a>Notes

L’élément linkedConfiguration > simplifie la gestion des assemblys de composants en permettant aux fichiers de configuration de l’application d’inclure des fichiers de configuration d’assembly dans des emplacements bien connus, plutôt que de dupliquer l’assembly [ **\<** ](linkedconfiguration-element.md) paramètres de configuration.

> [!NOTE]
> L’élément linkedConfiguration > n’est pas pris en charge pour les applications avec des manifestes côte à côte Windows.  **\<**

## <a name="example"></a>Exemple

L’exemple suivant montre comment inclure un fichier de configuration sur le disque dur local:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
