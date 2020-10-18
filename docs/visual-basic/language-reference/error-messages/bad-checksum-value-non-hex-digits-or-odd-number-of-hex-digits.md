---
title: Valeur de checksum erronée, pas de chiffre hexadécimal ou de nombre impair de chiffres hexadécimaux
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: e380033f9353781ee7dc86696e93c8d0f18a1a73
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162971"
---
# <a name="bc42033-bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a>BC42033 : valeur de somme de contrôle incorrecte, chiffres non hexadécimaux ou nombre impair de chiffres hexadécimaux

Une valeur de checksum contient des chiffres hexadécimaux non valides ou comporte un nombre impair de chiffres.

 Quand ASP.NET génère un fichier source Visual Basic (extension .vb), il calcule une checksum et la place dans un fichier source masqué, identifié par `#externalchecksum`. L'utilisateur peut également générer un fichier .vb pour effectuer cela, mais il est préférable de réserver ce processus à un usage interne.

 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID d’erreur :** BC42033

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Si ASP.NET génère le fichier source Visual Basic, redémarrez la génération du projet.

2. Si l'avertissement persiste après le redémarrage, réinstallez ASP.NET, puis réessayez la génération.

3. Si l'avertissement n'est toujours pas résolu, ou si vous n'utilisez pas ASP.NET, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.

## <a name="see-also"></a>Voir aussi

- [Présentation de ASP.NET](/aspnet/overview)
- [Nous contacter](/visualstudio/ide/feedback-options)
