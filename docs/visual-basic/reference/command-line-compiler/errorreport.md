---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: a9741f7a8283f8603e02dae5abea151c6ee5d75e
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775665"
---
# <a name="-errorreport"></a>-errorreport

Spécifie comment le compilateur Visual Basic doit signaler les erreurs internes du compilateur.

## <a name="syntax"></a>Syntaxe

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a>Notes

Cette option offre un moyen pratique de signaler un Visual Basic erreur interne du compilateur (ICE) à l’équipe Visual Basic chez Microsoft. Par défaut, le compilateur n’envoie aucune information à Microsoft. Toutefois, si vous rencontrez une erreur interne du compilateur, cette option vous permet de signaler l’erreur à Microsoft. Ces informations permettront aux ingénieurs Microsoft d’identifier la cause et peuvent contribuer à améliorer la prochaine version de Visual Basic.

La capacité d’un utilisateur à envoyer des rapports dépend des autorisations de la stratégie de l’ordinateur et de l’utilisateur.

Le tableau suivant résume l’effet de l' `-errorreport` option.

|Option|Comportement|
|---|---|
|`prompt`|Si une erreur interne du compilateur se produit, une boîte de dialogue s’affiche pour vous permettre d’afficher les données exactes collectées par le compilateur. Vous pouvez déterminer s’il existe des informations sensibles dans le rapport d’erreurs et si vous souhaitez les envoyer à Microsoft. Si vous décidez de l’envoyer et que les paramètres de stratégie de l’ordinateur et de l’utilisateur l’autorisent, le compilateur envoie les données à Microsoft.|
|`queue`|Met le rapport d’erreurs en file d’attente. Lorsque vous vous connectez avec des privilèges d’administrateur, vous pouvez signaler les échecs depuis la dernière connexion (vous n’êtes pas invité à envoyer des rapports pour les défaillances plus d’une fois tous les trois jours). Il s’agit du comportement par défaut `-errorreport` lorsque l’option n’est pas spécifiée.|
|`send`|Si une erreur interne du compilateur se produit et que les paramètres de stratégie de l’ordinateur et de l’utilisateur l’autorisent, le compilateur envoie les données à Microsoft.<br /><br /> L’option `-errorreport:send` tente d’envoyer automatiquement des informations sur les erreurs à Microsoft si la création de rapports est activée par les paramètres système [rapport d’erreurs Windows](/windows/desktop/wer/windows-error-reporting) . |
|`none`|Si une erreur interne du compilateur se produit, elle n’est pas collectée ou envoyée à Microsoft.|

Le compilateur envoie des données qui incluent la pile au moment de l’erreur, qui comprend généralement du code source. Si `-errorreport` est utilisé avec l’option [-bugreport (](../../../visual-basic/reference/command-line-compiler/bugreport.md) , alors l’intégralité du fichier source est envoyée.

Cette option est utilisée de manière optimale avec l’option [-bugreport (](../../../visual-basic/reference/command-line-compiler/bugreport.md) , car elle permet aux ingénieurs Microsoft de reproduire plus facilement l’erreur.

> [!NOTE]
> L' `-errorreport` option n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.

## <a name="example"></a>Exemple

Le code suivant tente de compiler `T2.vb`et, si le compilateur rencontre une erreur interne du compilateur, il vous invite à envoyer le rapport d’erreurs à Microsoft.

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
