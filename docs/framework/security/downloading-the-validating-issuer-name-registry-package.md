---
title: Téléchargement du package de validation du registre des noms d'émetteurs
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 5684844f1db33b075df099b3026d9d0c1061199f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631847"
---
# <a name="download-the-validating-issuer-name-registry-package"></a>Télécharger le Package de Registre de nom émetteur lors de la validation

Cette rubrique explique comment télécharger et utiliser le Registre des noms d’émetteurs de validation (VINR, Validating Issuer Name Registry) dans votre projet.

Le Registre VINR est disponible sous forme de package NuGet, qui ajoute les assemblys et les références nécessaires à votre projet. Si vous n’avez pas encore installé NuGet, accédez à [nuget.org](https://nuget.org) pour l’installer. Vous pouvez consulter l’historique de contrôle de version pour l’extension en visitant sa page sur NuGet : [Validation du Registre de nom de l’émetteur sur NuGet de Microsoft](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)

## <a name="use-the-package-manager-gui"></a>Utiliser l’interface utilisateur graphique du Gestionnaire de Package

1. Dans Visual Studio, cliquez sur votre projet dans l’**Explorateur de solutions**, puis sélectionnez **Gérer les packages NuGet**.

2. Dans la fenêtre **Gérer les packages NuGet**, cliquez sur la zone de recherche et tapez `ValidatingIssuerNameRegistry`, puis appuyez sur **Entrée**.

3. Dans le volet de résultats, cliquez sur le bouton **Installer** pour le premier résultat.

4. Le téléchargement du package commence. Avant l’ajout du package à votre projet, la boîte de dialogue d’acceptation de licence s’affiche. Si vous êtes d’accord avec les termes du contrat de licence, cliquez sur **Accepter**.

5. Les assemblys VINR les plus récents seront téléchargés et ajoutés à votre projet.

## <a name="use-the-package-manager-console"></a>Utilisez la Console du Gestionnaire de Package

1. Dans Visual Studio, cliquez sur **outils** > **Gestionnaire de Package NuGet** > **Console du Gestionnaire de Package**.

2. La **Console du Gestionnaire de package** s’affiche. Tapez le texte suivant et appuyez sur **Entrée** :

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. Les assemblys VINR les plus récents seront téléchargés et ajoutés à votre projet.
