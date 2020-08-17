---
title: -publicsign (Options du compilateur C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 2655e0216a412053e052ab2ec2fcc8c68ea4f968
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88268047"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (Options du compilateur C#)

Cette option force le compilateur à appliquer une clé publique sans signer l’assembly. L’option **-publicsign** définit également un bit dans l’assembly qui indique au runtime que le fichier est signé.

## <a name="syntax"></a>Syntaxe

```console
-publicsign
```

## <a name="arguments"></a>Arguments

Aucun.

## <a name="remarks"></a>Notes

L’option **-publicsign** nécessite l’utilisation de l’option [-keyfile](keyfile-compiler-option.md) ou [-keycontainer](keycontainer-compiler-option.md). Les options **keyfile** ou **keycontainer** spécifient la clé publique.

Les options **-publicsign** et **-delaysign** s’excluent mutuellement.

Parfois appelée « fausse signature » ou « signature OSS », la signature publique inclut la clé publique dans un assembly de sortie et définit l’indicateur « signé ». Toutefois, elle ne signe pas l’assembly avec une clé privée. Cette approche est utile dans le cadre de projets open source. Vous pouvez en effet générer des assemblys compatibles avec les assemblys publiés « totalement signés », même si vous n’avez pas accès à la clé privée utilisée pour les signer. Puisque pratiquement aucun consommateur ne doit vérifier si l’assembly est totalement signé, ces assemblys générés publiquement peuvent être utilisés dans la quasi-totalité des scénarios employant des assemblys totalement signés.

### <a name="to-set-this-compiler-option-in-a-csproj-file"></a>Pour définir cette option du compilateur dans un fichier csproj

Ouvrez le fichier. csproj pour un projet, puis ajoutez l’élément suivant :

```xml
<PublicSign>true</PublicSign>
```

## <a name="see-also"></a>Voir aussi

- [Option -delaysign du compilateur C#](delaysign-compiler-option.md)
- [Option -keyfile du compilateur C#](keyfile-compiler-option.md)
- [Option -keycontainer du compilateur C#](keycontainer-compiler-option.md)
- [Options du compilateur C#](index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
