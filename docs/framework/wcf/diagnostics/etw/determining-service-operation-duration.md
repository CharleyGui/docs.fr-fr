---
title: Détermination de la durée d'une opération de service
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 2607efe0d469f1235ee3d43d62f5e9781681668d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254829"
---
# <a name="determining-service-operation-duration"></a>Détermination de la durée d'une opération de service

Si le traçage analytique est activé dans une application Windows Communication Foundation (WCF), la durée d’exécution d’une opération de service peut être facilement déterminée en examinant le journal des événements.  Cette rubrique montre comment déterminer la durée d'exécution d'une opération de service.  
  
### <a name="determining-service-operation-execution-duration"></a>Détermination de la durée d'exécution d'une opération de service  
  
1. Ouvrez observateur d’événements en cliquant sur **Démarrer**, **exécuter**, puis en entrant `eventvwr.exe` .  
  
2. Si vous n’avez pas activé le traçage analytique, développez **journaux des applications et des services**, **Microsoft**, **Windows**, serveur d’applications **-applications**. Sélectionnez **Afficher**, **afficher les journaux d’analyse et de débogage**. Cliquez avec le bouton droit sur **analyse** et sélectionnez **activer le journal**. Laissez l'Observateur d'événements ouvert afin que les traces soient visibles après l'exécution de l'opération de service.  
  
3. Ensuite, ouvrez une application WCF qui comprend un projet de service et un projet client qui interagit avec ce service.  Vous pouvez créer une telle application en suivant le [didacticiel prise en main](../../getting-started-tutorial.md).  Si vous avez installé les exemples WCF, vous pouvez ouvrir le [prise en main](../../samples/getting-started-sample.md), qui contient le projet terminé créé dans le didacticiel.  
  
4. Exécutez l’application serveur en appuyant sur **F5**. Exécutez l’application cliente en cliquant avec le bouton droit sur le projet **client** et en sélectionnant **Déboguer**, **Démarrer une nouvelle instance**.  
  
5. Dans l'Observateur d'événements, actualisez le journal Analyse et triez les événements par ID d'événement.  Recherchez les événements avec l’ID d’événement [214-OperationCompleted](214-operationcompleted.md).  Ces événements affichent les opérations terminées et leur durée.  L'événement suivant affiche la durée d'une opération d'ajout.  
  
    ```output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
