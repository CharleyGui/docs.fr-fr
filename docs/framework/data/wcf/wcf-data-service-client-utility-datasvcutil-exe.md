---
title: Utilitaire client des services de données WCF (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 1348ba73eb87a140b42e3565b4388a70f1f47ca1
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802014"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>Utilitaire client des services de données WCF (DataSvcUtil.exe)

Outil DataSvcUtil. exe est un outil de ligne de commande fourni par WCF Data Services qui consomme un flux Open Data Protocol (OData) et génère les classes de service de données client nécessaires pour accéder à un service de données à partir d’une application cliente .NET Framework. Cet utilitaire peut générer des classes de données à l'aide des sources de métadonnées suivantes :

- URI racine d'un service de données. L'utilitaire demande le document des métadonnées du service, qui décrit le modèle de données exposé par le service de données. Pour plus d’informations, consultez [AtomPub (RFC5023)](https://tools.ietf.org/html/rfc5023#section-8).

- Un fichier de modèle de données (. CSDL) défini à l’aide de l’Conceptual Schema Definition Language (CSDL), tel que défini dans la spécification de [format de fichier de définition de schéma conceptuel de\[MC-csdl\]:](https://docs.microsoft.com/openspecs/windows_protocols/mc-csdl/c03ad8c3-e8b7-4306-af96-a9e52bb3df12) .

- Fichier .edmx créé à l'aide des outils Entity Data Model fournis avec l'Entity Framework. Pour plus d’informations, consultez la spécification [\[MC-EDMX\]: Entity Data Model pour le format d’Empaquetage Data Services](https://docs.microsoft.com/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16) .

Pour plus d’informations, consultez [Comment : générer manuellement des classes de service de données client](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).

L’outil outil DataSvcUtil. exe est installé dans le répertoire .NET Framework. Dans de nombreux cas, il se trouve dans *C:\Windows\Microsoft.NET\Framework\v4.0*. Pour les systèmes 64 bits, il se trouve dans *C:\Windows\Microsoft.NET\Framework64\v4.0*. Vous pouvez également accéder à l’outil outil DataSvcUtil. exe à partir de Invite de commandes développeur pour Visual Studio.

## <a name="syntax"></a>Syntaxe

```console
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a>Parameters

|Option|Description|
|------------|-----------------|
|`/dataservicecollection`|Spécifie que le code nécessaire pour lier des objets aux contrôles est également généré.|
|`/help`<br /><br /> \- ou -<br /><br /> `/?`|Affiche la syntaxe et les options de commande de l'outil.|
|`/in:` *\<file>*|Spécifie le fichier .csdl ou .edmx ou un répertoire qui contient le fichier.|
|`/language:`[VB&#124;CSharp]|Spécifie le langage des fichiers de code source générés. Le langage par défaut est C#.|
|`/nologo`|Supprime l'affichage du message de copyright.|
|`/out:` *\<file>*|Spécifie le nom du fichier de code source qui contient les classes de service de données client générées.|
|`/uri:` *\<string>*|URI du flux OData.|
|`/version:`[1.0&#124;2.0]|Spécifie la version la plus élevée acceptée d’OData. La version est déterminée en fonction de l’attribut `DataServiceVersion` de l’élément DataService dans les métadonnées du service de données retournées. Pour plus d’informations, consultez contrôle de [version des services de données](data-service-versioning-wcf-data-services.md). Lorsque vous spécifiez le paramètre `/dataservicecollection`, vous devez également spécifier `/version:2.0` pour activer la liaison de données.|

## <a name="see-also"></a>Voir aussi

- [Génération de la bibliothèque cliente du service de données](generating-the-data-service-client-library-wcf-data-services.md)
- [Guide pratique pour ajouter une référence de services de données](how-to-add-a-data-service-reference-wcf-data-services.md)
