---
title: 'NETSDK1004 : fichier de ressources introuvable'
description: En savoir plus sur l’erreur du kit de développement logiciel (SDK) .NET NETSDK1004, qui se produit lorsque l' project.assets.jssur le fichier est introuvable.
ms.topic: error-reference
ms.date: 01/26/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: ed42ad0e8ebef7362cc029125fe51d3f300acbae
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98900359"
---
# <a name="netsdk1004-assets-file-not-found"></a>NETSDK1004 : fichier de ressources introuvable

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 2.1.100 .net Core et versions ultérieures

Cette erreur se produit lorsque le fichier *de ressourcesproject.assets.jssur* est introuvable lors de la génération. Le message d’erreur complet est semblable à ce qui suit :

**NETSDK1004 : le fichier de ressources' C:\IncorrectPath\project.assets.json’est introuvable. Exécutez une restauration de package NuGet pour générer ce fichier.**

Vous pouvez rencontrer un avertissement NETSDK1004 si vous exécutez la `dotnet build` commande à partir d’un chemin d’accès de répertoire contenant un `%` caractère.
