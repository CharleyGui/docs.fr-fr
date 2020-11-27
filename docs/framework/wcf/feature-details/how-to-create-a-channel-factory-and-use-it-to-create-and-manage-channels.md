---
title: 'Procédure : créer une fabrique de canaux et l’utiliser pour créer et gérer des canaux'
ms.date: 03/30/2017
ms.assetid: 018dcc30-9f61-419e-af8e-412a85e8d282
ms.openlocfilehash: 44b0f45d1a340b8e8229ded827ad3ded738ae677
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256779"
---
# <a name="how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels"></a>Procédure : créer une fabrique de canaux et l’utiliser pour créer et gérer des canaux

La classe <xref:System.ServiceModel.DuplexChannelFactory%601> offre des outils qui permettent de créer et de gérer des canaux duplex de différents types utilisés ensuite par les clients pour envoyer des messages vers des points de terminaison de service ou en recevoir à partir de ces mêmes points.  
  
## <a name="example"></a> Exemple  

 L'exemple de code suivant indique comment créer une fabrication de canal et l'utiliser ensuite pour créer et gérer des canaux.  
  
 [!code-csharp[S_CustomAuthentication#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_customauthentication/cs/instance.cs#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.DuplexChannelFactory%601>
