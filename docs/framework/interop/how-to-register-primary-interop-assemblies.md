---
title: 'Procédure : enregistrer des assemblys PIA'
description: Inscrivez les assemblys PIA à l’aide de l’outil Assembly Registration Tool (Regasm.exe) et découvrez d’autres problèmes liés aux assemblys d’interopérabilité.
ms.date: 03/30/2017
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
ms.openlocfilehash: 09b283712a66805669154c720dff5c2c5f910bf4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547178"
---
# <a name="how-to-register-primary-interop-assemblies"></a>Procédure : enregistrer des assemblys PIA

Les classes ne peuvent être marshalées que par COM Interop et sont toujours marshalées en tant qu’interfaces. Dans certains cas, l’interface utilisée pour marshaler la classe est appelée interface de classe. Pour plus d’informations sur la substitution de l’interface de classe par une interface de votre choix, consultez [Wrapper CCW (COM Callable Wrapper)](../../standard/native-interop/com-callable-wrapper.md).

 Même s'il est possible d'utiliser des types COM à partir d'une application .NET Framework pour générer un assembly d'interopérabilité, une telle utilisation pose problème. Chaque fois qu'un développeur importe et signe une bibliothèque de types COM, il crée un ensemble de types uniques qui sont incompatibles avec ceux importés et signés par un autre développeur. La solution à ce problème d'incompatibilité de type est, pour chaque développeur, d'obtenir l'assembly PIA signé et fourni par le fournisseur.

 Si vous envisagez d'exposer des types COM tiers à d'autres applications, utilisez toujours l'assembly PIA fourni par le même éditeur que la bibliothèque de types qu'il définit. En plus de garantir la compatibilité des types, les assemblys PIA sont souvent personnalisés par le fournisseur pour améliorer l'interopérabilité.

 Même si vous ne souhaitez pas exposer des types COM tiers, l’utilisation d’un assembly PIA peut faciliter l’interopérabilité avec les composants COM. Toutefois, cette stratégie ne protège pas des modifications qu'un fournisseur peut apporter aux types définis dans un assembly PIA. Si votre application nécessite une telle protection, générez votre propre assembly d'interopérabilité au lieu d'utiliser un assembly PIA.

 Vous devez inscrire tous les assemblys PIA acquis sur votre ordinateur de développement avant de pouvoir les référencer avec Visual Studio. Visual Studio recherche et utilise un assembly PIA la première fois que vous référencez un type à partir d'une bibliothèque de types COM. Si Visual Studio ne peut pas localiser l'assembly PIA associé à la bibliothèque de types, il vous invite à l'acquérir ou vous propose de créer un assembly d'interopérabilité . De même, l’outil [Tlbimp.exe (importateur de bibliothèques de types)](../tools/tlbimp-exe-type-library-importer.md) utilise également le Registre pour rechercher des assemblys PIA.

 Même s'il n'est pas nécessaire d'inscrire les assemblys PIA si vous ne prévoyez pas d'utiliser Visual Studio, l'inscription offre deux avantages :

- Un assembly PIA inscrit est clairement marqué sous la clé de Registre de la bibliothèque de types d'origine. L'inscription est le meilleur moyen de rechercher un assembly PIA sur votre ordinateur.

- Vous pouvez éviter de générer et d'utiliser par erreur un nouvel assembly d'interopérabilité si, à un moment donné, vous utilisez Visual Studio pour référencer un type pour lequel vous avez un assembly PIA non inscrit.

Utilisez l’outil [Regasm.exe (outil d’inscription d’assemblys)](../tools/regasm-exe-assembly-registration-tool.md) pour inscrire un assembly PIA.

## <a name="to-register-a-primary-interop-assembly"></a>Pour inscrire un assembly PIA

1. À l’invite de commandes, tapez :

     **regasm** *nomassembly*

     Dans cette commande, *nomassembly* est le nom de fichier de l’assembly inscrit. Regasm.exe ajoute une entrée pour l'assembly PIA sous la même clé de Registre que la bibliothèque de types d'origine.

## <a name="example"></a> Exemple
 L'exemple suivant inscrit l'assembly PIA `CompanyA.UtilLib.dll`.

```console
regasm CompanyA.UtilLib.dll
```

## <a name="see-also"></a>Voir aussi

- [Programmer avec des assemblys PIA](/previous-versions/dotnet/netframework-4.0/baxfadst(v=vs.100))
- [Rechercher des assemblys PIA](/previous-versions/dotnet/netframework-4.0/y06sxw56(v=vs.100))
- [Redistribuer des assemblys PIA](/previous-versions/dotnet/netframework-4.0/w0dt2w20(v=vs.100))
