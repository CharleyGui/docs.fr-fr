---
title: 'Procédure : Ajouter une référence de service de données (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790736"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Procédure : Ajouter une référence de service de données (WCF Data Services)

Vous pouvez utiliser la boîte de dialogue **Ajouter une référence de service** dans Visual Studio pour ajouter une référence à WCF Data Services. De cette manière, vous pouvez accéder plus facilement à un service de données dans une application cliente que vous développez dans Visual Studio. Lorsque vous complétez cette procédure, les classes de données sont générées selon les métadonnées obtenues auprès du service de données. Pour plus d’informations, consultez [génération de la bibliothèque cliente du service de données](generating-the-data-service-client-library-wcf-data-services.md).

## <a name="add-a-data-service-reference"></a>Ajouter une référence de service de données

1. (Facultatif) Si le service de données n'appartient pas à la solution et n'est pas déjà en cours d'exécution, démarrez le service de données et notez l'URI du service de données.

2. Dans Visual Studio, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet client, puis sélectionnez **Ajouter** > une**référence de service**.

3. Si le service de données fait partie de la solution actuelle, cliquez sur **découvrir**.

     ou

     Dans la zone de texte **adresse** , tapez l’URL de base du service de données, `http://localhost:1234/Northwind.svc`par exemple, puis cliquez sur **OK**.

4. Sélectionnez **OK**.

     Un nouveau fichier de code qui contient les classes de données qui peuvent accéder aux ressources du service de données et interagir avec celles-ci est ajouté au projet.

## <a name="see-also"></a>Voir aussi

- [Démarrage rapide](quickstart-wcf-data-services.md)
