---
title: 'Procédure : Générer manuellement des classes de service de données client (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: f8d99213a1ef98c48855ba9f561f87a800768c89
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894298"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>Procédure : Générer manuellement des classes de service de données client (WCF Data Services)
WCF Data Services s’intègre à Visual Studio pour vous permettre de générer automatiquement des classes de service de données client lorsque vous utilisez la boîte de dialogue **Ajouter une référence de service** pour ajouter une référence à un service de données dans un projet Visual Studio. Pour plus d’informations, consultez [Guide pratique pour Ajoutez une référence](how-to-add-a-data-service-reference-wcf-data-services.md)de service de données. Vous pouvez également générer manuellement les mêmes classes de service de données client en utilisant l'outil de génération de code, `DataSvcUtil.exe`. Cet outil, inclus dans WCF Data Services, génère des classes .NET Framework à partir de la définition du service de données. Il peut également être utilisé pour générer des classes de service des données depuis le fichier de modèle conceptuel (.csdl) et depuis le fichier .edmx qui représente un modèle Entity Framework dans un projet Visual Studio.

 L'exemple dans cette rubrique crée des classes de service de données client basées sur l'exemple de service de données Northwind. Ce service est créé lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md). Certains exemples dans cette rubrique requièrent le fichier modèle conceptuel pour le modèle Northwind. Pour plus d'informations, voir [Procédure : Utilisez EdmGen. exe pour générer les fichiers](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)de modèle et de mappage. Certains exemples dans cette rubrique requièrent le fichier .edmx pour le modèle Northwind. Pour plus d’informations, consultez [vue d’ensemble du fichier. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).

### <a name="to-generate-c-classes-that-support-data-binding"></a>Pour générer des classes C# qui prennent en charge la liaison de données

- À l'invite de commandes, exécutez la commande suivante sans saut de ligne :

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Vous devez remplacer la valeur fournie au paramètre `/uri:` par l'URI de l'instance de votre exemple de service de données Northwind .

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>Pour générer des classes Visual Basic qui prennent en charge la liaison de données

- À l'invite de commandes, exécutez la commande suivante sans saut de ligne :

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Vous devez remplacer la valeur fournie au paramètre `/uri:` par l'URI de l'instance de votre exemple de service de données Northwind .

### <a name="to-generate-c-classes-based-on-the-service-uri"></a>Pour générer des classes C# basées sur l'URI de service

- À l'invite de commandes, exécutez la commande suivante sans saut de ligne :

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Vous devez remplacer la valeur fournie au paramètre `/uri:` par l'URI de l'instance de votre exemple de service de données Northwind .

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>Pour générer des classes Visual Basic basées sur l'URI de service

- À l'invite de commandes, exécutez la commande suivante sans saut de ligne :

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Vous devez remplacer la valeur fournie au paramètre `/uri:` par l'URI de l'instance de votre exemple de service de données Northwind .

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>Pour générer des classes C# basées sur le fichier de modèle conceptuel (CSDL)

- À l'invite de commandes, exécutez la commande suivante sans saut de ligne :

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>Pour générer des classes Visual Basic basées sur le fichier de modèle conceptuel (CSDL)

- À l'invite de commandes, exécutez la commande suivante sans saut de ligne :

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>Pour générer des classes C# basées sur le fichier .edmx

- À l'invite de commandes, exécutez la commande suivante sans saut de ligne :

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>Pour générer des classes Visual Basic basées sur le fichier .edmx

- À l'invite de commandes, exécutez la commande suivante sans saut de ligne :

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a>Voir aussi

- [Génération de la bibliothèque cliente du service de données](generating-the-data-service-client-library-wcf-data-services.md)
- [Guide pratique pour Ajouter une référence de service de données](how-to-add-a-data-service-reference-wcf-data-services.md)
- [Utilitaire client des services de données WCF (DataSvcUtil.exe)](wcf-data-service-client-utility-datasvcutil-exe.md)
