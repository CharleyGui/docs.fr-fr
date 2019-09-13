---
title: Utilitaire client des services de données WCF (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 7632362339cf9e23599f4f688f98cbc1d0b32114
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894248"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>Utilitaire client des services de données WCF (DataSvcUtil.exe)

Outil DataSvcUtil. exe est un outil de ligne de commande fourni par WCF Data Services qui consomme [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] un flux et génère les classes de service de données client nécessaires pour accéder à un service de données à partir d’une application cliente .NET Framework. Cet utilitaire peut générer des classes de données à l'aide des sources de métadonnées suivantes :

- URI racine d'un service de données. L'utilitaire demande le document des métadonnées du service, qui décrit le modèle de données exposé par le service de données. Pour plus d’informations, [consultez OData : Document](https://go.microsoft.com/fwlink/?LinkId=186070)de métadonnées du service.

- Un fichier de modèle de données (. CSDL) défini à l’aide du Conceptual Schema Definition Language (CSDL), tel [que défini dans\] \[MC-CSDL : Spécification de format](https://go.microsoft.com/fwlink/?LinkID=159072) de fichier de définition de schéma conceptuel.

- Fichier .edmx créé à l'aide des outils Entity Data Model fournis avec l'Entity Framework. Pour plus d’informations, voir [ \[MC-edmx\]: Entity Data Model pour la spécification de](https://go.microsoft.com/fwlink/?LinkID=178833) format d’empaquetage Data Services.

Pour plus d’informations, consultez [Guide pratique pour Générez manuellement des classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)de service de données client.

L’outil outil DataSvcUtil. exe est installé dans le répertoire .NET Framework. Dans de nombreux cas, il se trouve dans *C:\Windows\Microsoft.NET\Framework\v4.0*. Pour les systèmes 64 bits, il se trouve dans *C:\Windows\Microsoft.NET\Framework64\v4.0*. Vous pouvez également accéder à l’outil outil DataSvcUtil. exe à partir de Invite de commandes développeur pour Visual Studio.

## <a name="syntax"></a>Syntaxe

```console
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a>Paramètres

|Option|Description|
|------------|-----------------|
|`/dataservicecollection`|Spécifie que le code nécessaire pour lier des objets aux contrôles est également généré.|
|`/help`<br /><br /> ou<br /><br /> `/?`|Affiche la syntaxe et les options de commande de l'outil.|
|`/in:` *\<file>*|Spécifie le fichier .csdl ou .edmx ou un répertoire qui contient le fichier.|
|`/language:`[VB&#124;CSharp]|Spécifie le langage des fichiers de code source générés. Le langage par défaut est C#.|
|`/nologo`|Supprime l'affichage du message de copyright.|
|`/out:` *\<file>*|Spécifie le nom du fichier de code source qui contient les classes de service de données client générées.|
|`/uri:` *\<string>*|URI du flux OData.|
|`/version:`[1.0&#124;2.0]|Spécifie la version la plus élevée acceptée d’OData. La version est déterminée en fonction de `DataServiceVersion` l’attribut de l’élément DataService dans les métadonnées du service de données retournées. Pour plus d’informations, consultez contrôle de [version des services de données](data-service-versioning-wcf-data-services.md). Lorsque vous spécifiez `/dataservicecollection` le paramètre, vous devez également `/version:2.0` spécifier pour activer la liaison de données.|

## <a name="see-also"></a>Voir aussi

- [Génération de la bibliothèque cliente du service de données](generating-the-data-service-client-library-wcf-data-services.md)
- [Guide pratique pour Ajouter une référence de service de données](how-to-add-a-data-service-reference-wcf-data-services.md)
