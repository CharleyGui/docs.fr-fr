---
title: 'Procédure : Utiliser EdmGen.exe pour valider les fichiers de modèle et les fichiers de mappage'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 62a3bde9d2431b9e9e86e2a8d8896520f3456590
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198117"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a>Procédure : Utiliser EdmGen.exe pour valider les fichiers de modèle et les fichiers de mappage

Cette rubrique montre comment utiliser l’outil [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) pour valider les fichiers de modèle et de mappage. Pour plus d’informations, consultez [Entity Data Model](../entity-data-model.md).  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a>Pour valider le modèle School à l'aide d'EdmGen.exe  
  
1. Créez la base de données School. Pour plus d’informations, consultez [création de l’exemple de base de données School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Générez le modèle School. Pour plus d’informations, consultez [Comment : utiliser EdmGen.exe pour générer les fichiers de modèle et de mappage](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Comment : configurer manuellement un projet Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Outils de Entity Data Model ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Comment : prégénérer les vues pour améliorer les performances des requêtes](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Procédure : Utiliser EdmGen.exe pour générer le code de couche objet](how-to-use-edmgen-exe-to-generate-object-layer-code.md)
