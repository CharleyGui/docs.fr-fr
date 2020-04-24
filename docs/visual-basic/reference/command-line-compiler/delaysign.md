---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 3ee94df096b756be544964cfbbd405355e3f728f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581269"
---
# <a name="-delaysign"></a>-delaysign

Spécifie si l'assembly sera complètement ou partiellement signé.

## <a name="syntax"></a>Syntaxe

```console
-delaysign[+ | -]
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`  
Facultatif. Utilisez `-delaysign-` si vous souhaitez obtenir un assembly complètement signé. Utilisez `-delaysign+` si vous souhaitez placer la clé publique dans l’assembly et réserver de l’espace pour le hachage signé. Par défaut, il s’agit de `-delaysign-`.

## <a name="remarks"></a>Notes

L' `-delaysign` option n’a aucun effet, sauf si elle est utilisée avec [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) ou [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).

Quand vous demandez un assembly totalement signé, le compilateur hache le fichier qui contient le manifeste (métadonnées de l’assembly) et signe ce hachage avec la clé privée. La signature numérique obtenue est stockée dans le fichier qui contient le manifeste. Lorsqu’un assembly est signé différé, le compilateur ne calcule pas et ne stocke pas la signature, mais réserve de l’espace dans le fichier afin que la signature puisse être ajoutée ultérieurement.

Par exemple, en utilisant `-delaysign+`, un développeur dans une organisation peut distribuer des versions de test non signées d’un assembly que les testeurs peuvent inscrire auprès du global assembly cache et utiliser. Lorsque le travail sur l’assembly est terminé, la personne responsable de la clé privée de l’organisation peut signer complètement l’assembly. Ce cloisonnement empêche la divulgation de la clé privée de l’organisation, tout en permettant à tous les développeurs de travailler sur les assemblys.

Pour plus d’informations sur la signature d’un assembly [, consultez Création et utilisation d’assemblys avec nom fort](../../../standard/assembly/create-use-strong-named.md) .

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>Pour définir-delaysign dans l’environnement de développement intégré Visual Studio

1. Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Signature** .

3. Définissez la valeur dans la zone **différer la signature uniquement** .

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
