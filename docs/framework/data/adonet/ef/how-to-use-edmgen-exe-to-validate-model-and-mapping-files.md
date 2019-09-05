---
title: 'Procédure : Utiliser EdmGen.exe pour valider les fichiers de modèle et les fichiers de mappage'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 4495ff3c5d55779e9db113a2a59361b643841382
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251379"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a>Procédure : Utiliser EdmGen.exe pour valider les fichiers de modèle et les fichiers de mappage
Cette rubrique montre comment utiliser l’outil [EDM Generator (EdmGen. exe)](edm-generator-edmgen-exe.md) pour valider les fichiers de modèle et de mappage. Pour plus d’informations, consultez [Entity Data Model](../entity-data-model.md).  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a>Pour valider le modèle School à l'aide d'EdmGen.exe  
  
1. Créez la base de données School. Pour plus d’informations, consultez [création de l’exemple de base de données School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Générez le modèle School. Pour plus d’informations, consultez [Guide pratique pour Utilisez EdmGen. exe pour générer les fichiers](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)de modèle et de mappage.  
  
3. À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique : Configurer manuellement un projet Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Outils de Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Guide pratique pour Prégénérer des vues pour améliorer les performances des requêtes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Guide pratique pour Utiliser EdmGen. exe pour générer le code de couche objet](how-to-use-edmgen-exe-to-generate-object-layer-code.md)
