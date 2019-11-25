---
title: Usage of Serialization Binder
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: bfce2a14c8757250c520919c8ff2a4d7048a9d5c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138647"
---
# <a name="usage-of-serialization-binder"></a>Usage of Serialization Binder
Cet exemple montre comment utiliser le <xref:System.Runtime.Serialization.SerializationBinder> pour modifier la version d'un type générique lorsqu'il est sérialisé.  
  
## <a name="demonstrates"></a>Démonstrations  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Discussion  
 Cet exemple montre comment deux entités ciblant différentes versions du .NET Framework peuvent communiquer à l’aide du formateur binaire et du Binder de sérialisation.  
  
Cet exemple a été développé à l’aide de .NET Remoting. Il se compose d’un serveur ciblant .NET Framework 4, qui implémente un contrat avec des types génériques, et deux clients différents, un ciblant .NET Framework 2,0 et un autre ciblant .NET Framework 4.  
  
 Le serveur attache un <xref:System.Runtime.Serialization.SerializationBinder> au formateur binary pour être en mesure de modifier la version des types en conséquence lors de la sérialisation, si les deux clients peuvent désérialiser correctement ces types.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Pour exécuter le client, cliquez avec le bouton droit sur la solution, SBGenericsVTS (6 projets), puis sélectionnez **Propriétés**.  
  
2. Dans **Propriétés communes**, sélectionnez **projet de démarrage**, puis sélectionnez **plusieurs projets de démarrage**.  
  
3. Sélectionnez le **serveur** en premier, puis **Client20** , puis **Client40**. Sélectionnez l’action **Démarrer** sur ces trois projets et laissez le reste défini sur **aucun**.  
  
4. Cliquez sur **OK** , puis appuyez sur F5 pour exécuter l’exemple.
