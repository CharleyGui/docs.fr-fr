---
title: 'Comment : utiliser EdmGen.exe pour générer les fichiers de modèle et les fichiers de mappage'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: ee8297c0833378b2b44800355b47db9caa2dc7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150510"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Comment : utiliser EdmGen.exe pour générer les fichiers de modèle et les fichiers de mappage
Cette rubrique montre comment utiliser l'outil EDM Generator (EdmGen.exe) pour générer les fichiers suivants à partir de la base de données School :  
  
- un modèle conceptuel (fichier .csdl) ;  
  
- un modèle de stockage (fichier .ssdl) ;  
  
- un mappage entre les modèles conceptuel et de stockage (fichier .msl) ;  
  
- du code de couche objet en Visual Basic ou C# ;  
  
- des fichiers de vue.  
  
 L'outil EdmGen.exe utilise la commande /mode:FullGeneration pour générer les fichiers répertoriés ci-dessus. Pour plus d’informations sur les commandes EdmGen.exe, voir [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md).  
  
 Si vous utilisez EdmGen.exe pour générer le modèle et la cartographie des fichiers, vous devez toujours configurer votre projet Visual Studio pour utiliser le cadre d’entité. Pour plus d’informations, voir [Comment configurer manuellement un projet-cadre d’entité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
> [!NOTE]
> Un modèle conceptuel généré par EdmGen.exe comprend tous les objets de la base de données. Si vous souhaitez générer un modèle conceptuel qui ne comporte que des objets spécifiques, utilisez l'Assistant EDM. Pour plus d’informations, voir [Comment : Utilisez l’Assistant modèle de données d’entité.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Pour générer à l'aide de l'outil EdmGen.exe le modèle School pour un projet Visual Basic  
  
1. Créez la base de données School. Pour plus d’informations, voir [Créer la base de données sur les échantillons d’écoles](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Pour générer à l'aide de l'outil EdmGen.exe le modèle School pour un projet C#  
  
1. Créez la base de données School. Pour plus d’informations, voir [Créer la base de données sur les échantillons d’écoles](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Modélisation et mappage](modeling-and-mapping.md)
- [Comment : configurer manuellement un projet Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Comment : prégénérer les vues pour améliorer les performances des requêtes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [ADO.NET outils de modèle de données d’entité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Guide pratique pour utiliser EdmGen.exe pour valider les fichiers de modèle et les fichiers de mappage](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
