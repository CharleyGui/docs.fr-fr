---
title: 'Procédure : Utiliser EdmGen.exe pour générer des fichiers de modèle et des fichiers de mappage'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 141b19c545360f92c2689252cf9aefd1ef156cf0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251420"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Procédure : Utiliser EdmGen.exe pour générer des fichiers de modèle et des fichiers de mappage
Cette rubrique montre comment utiliser l'outil EDM Generator (EdmGen.exe) pour générer les fichiers suivants à partir de la base de données School :  
  
- un modèle conceptuel (fichier .csdl) ;  
  
- un modèle de stockage (fichier .ssdl) ;  
  
- un mappage entre les modèles conceptuel et de stockage (fichier .msl) ;  
  
- du code de couche objet en Visual Basic ou C# ;  
  
- des fichiers de vue.  
  
 L'outil EdmGen.exe utilise la commande /mode:FullGeneration pour générer les fichiers répertoriés ci-dessus. Pour plus d’informations sur les commandes EdmGen. exe, consultez [EDM Generator (EdmGen. exe)](edm-generator-edmgen-exe.md).  
  
 Si vous utilisez EdmGen. exe pour générer les fichiers de modèle et de mappage, vous devez toujours configurer votre projet Visual Studio pour utiliser [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]le. Pour plus d’informations, consultez [Guide pratique pour Configurez manuellement un](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))projet Entity Framework.  
  
> [!NOTE]
> Un modèle conceptuel généré par EdmGen.exe comprend tous les objets de la base de données. Si vous souhaitez générer un modèle conceptuel qui ne comporte que des objets spécifiques, utilisez l'Assistant EDM. Pour plus d’informations, consultez [Guide pratique pour Utilisez l’Assistant](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Pour générer à l'aide de l'outil EdmGen.exe le modèle School pour un projet Visual Basic  
  
1. Créez la base de données School. Pour plus d’informations, consultez [création de l’exemple de base de données School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Pour générer à l'aide de l'outil EdmGen.exe le modèle School pour un projet C#  
  
1. Créez la base de données School. Pour plus d’informations, consultez [création de l’exemple de base de données School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Modélisation et mappage](modeling-and-mapping.md)
- [Guide pratique pour Configurer manuellement un projet Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Guide pratique pour Prégénérer des vues pour améliorer les performances des requêtes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Outils de Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Guide pratique pour Utiliser EdmGen. exe pour valider les fichiers de modèle et de mappage](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
