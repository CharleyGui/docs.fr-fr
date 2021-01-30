---
title: 'NETSDK1004 : fichier de ressources introuvable'
description: En savoir plus sur l’erreur du kit de développement logiciel (SDK) .NET NETSDK1004, qui se produit lorsque l' project.assets.jssur le fichier est introuvable.
ms.topic: error-reference
ms.date: 01/29/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: 8416063fe318106cbcb4dbccacef3ecaaff5bba2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216433"
---
# <a name="netsdk1004-assets-file-not-found"></a>NETSDK1004 : fichier de ressources introuvable

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 2.1.100 .net Core et versions ultérieures

NuGet écrit un fichier nommé *project.assets.js* dans le dossier *obj* , et le kit de développement logiciel (SDK) .net l’utilise pour obtenir des informations sur les packages à passer au compilateur. Cette erreur se produit lorsque le fichier *de ressourcesproject.assets.jssur* est introuvable lors de la génération. Le message d’erreur complet est semblable à l’exemple suivant :

**NETSDK1004 : le fichier de ressources' C:\path\to\project.assets.json’est introuvable. Exécutez une restauration de package NuGet pour générer ce fichier.**

Voici quelques causes possibles de l’erreur :

* Vous exécutez la `dotnet build` commande à partir d’un chemin d’accès de répertoire contenant un `%` caractère. Pour résoudre l’erreur, supprimez du `%` nom de dossier, puis réexécutez `dotnet build` .
* Une modification apportée au fichier projet n’a pas été automatiquement détectée et restaurée par le système de projet. Pour résoudre l’erreur, ouvrez une invite de commandes et exécutez `dotnet restore` sur le projet.
* Un projet a été restauré séparément par une version antérieure de Nuget.exe. Pour résoudre l’erreur, ouvrez une invite de commandes et exécutez `dotnet restore` sur le projet.
* Une erreur antérieure, telle que NETSDK1045 (la version du kit de développement logiciel (SDK) que vous utilisez ne prend pas en charge le Framework cible du projet), a empêché NuGet de créer le fichier de ressources du projet. Pour résoudre l’erreur NETSDK1004, résolvez l’erreur antérieure, puis exécutez `dotnet restore` sur le projet.
* App Center CI crée un projet qui a un assembly externe qui n’est pas dans NuGet. Pour résoudre l’erreur, utilisez un package NuGet pour l’assembly.
