---
description: -errorreport (Options du compilateur C#)
title: -errorreport (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 6238ac392ff99d18d9cc7ea07e23b08ff235c14f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173228"
---
# <a name="-errorreport-c-compiler-options"></a>-errorreport (Options du compilateur C#)

Cette option fournit un moyen pratique de signaler une erreur interne du compilateur C# à Microsoft.

> [!NOTE]
> Sur Windows Vista et Windows Server 2008, les paramètres de rapport d’erreurs que vous spécifiez pour Visual Studio ne remplacent pas les paramètres définis par l’intermédiaire de Rapport d’erreurs Windows. Les paramètres de Rapport d’erreurs Windows ont toujours priorité sur les paramètres de signalement d’erreurs de Visual Studio.

## <a name="syntax"></a>Syntaxe

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a>Arguments

 **Aucune**  
 Les rapports sur les erreurs internes du compilateur ne seront pas collectés ni envoyés à Microsoft.

 **invite** Vous invite à envoyer un rapport lorsque vous recevez une erreur interne du compilateur. **prompt** est la valeur par défaut quand vous compilez une application dans l’environnement de développement.

 **file d’attente** Met en file d’attente le rapport d’erreurs. Quand vous ouvrez une session avec des informations d’identification administratives, vous pouvez signaler toute défaillance qui s’est produite depuis votre dernière connexion. Vous ne serez pas invité à envoyer des rapports d’échecs plus d’une fois tous les trois jours. **queue** est la valeur par défaut quand vous compilez une application à partir de la ligne de commande.

 **Envoyer** Envoie automatiquement des rapports d’erreurs internes du compilateur à Microsoft. Pour activer cette option, vous devez tout d’abord accepter la politique de collecte de données de Microsoft. La première fois que vous spécifiez **-errorreport:send** sur un ordinateur, un message du compilateur vous dirige vers un site web qui affiche la politique de collecte de données de Microsoft.

## <a name="remarks"></a>Notes

 Une erreur interne du compilateur se produit quand le compilateur ne peut pas traiter un fichier de code source. Quand une telle erreur se produit, le compilateur ne génère pas de fichier de sortie ni de diagnostic utile que vous pouvez utiliser pour corriger votre code.

 Dans les versions précédentes, quand vous receviez une erreur interne du compilateur, vous étiez invité à contacter le Support technique Microsoft pour signaler le problème. En utilisant **-errorreport**, vous pouvez fournir des informations sur l’erreur interne du compilateur à l’équipe Visual C#. Vos rapports d’erreurs peuvent aider à améliorer les versions ultérieures du compilateur.

 La capacité d’un utilisateur à envoyer des rapports dépend des autorisations de stratégie ordinateur et utilisateur.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la page **Propriétés** du projet. Pour plus d’informations, consultez [Générer, page du Concepteur de projets (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).

2. Cliquez sur la page de propriétés **Générer**.

3. Cliquez sur le bouton **Avancé** .

4. Modifiez la propriété **Rapport d’erreurs du compilateur interne**.

 Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.

## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
