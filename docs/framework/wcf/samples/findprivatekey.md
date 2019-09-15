---
title: Exemple FindPrivateKey-WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 4ba4316489c1494da9421bea5c513e44c6eb50a7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989883"
---
# <a name="findprivatekey-sample"></a>Exemple FindPrivateKey

Il peut être difficile de rechercher l'emplacement et le nom du fichier de clé privée associé à un certificat X.509 spécifique dans le magasin de certificats. L'outil FindPrivateKey.exe facilite ce processus.

> [!IMPORTANT]
> FindPrivateKey est un exemple qui doit être compilé avant son utilisation. Consultez la section [pour générer le projet FindPrivateKey](#to-build-the-findprivatekey-project) pour obtenir des instructions sur la façon de générer l’outil FindPrivateKey.

Les certificats X.509 sont installés par un administrateur ou tout utilisateur sur l'ordinateur. Toutefois, un service s’exécutant sous un compte différent peut accéder au certificat. Par exemple, le compte SERVICE réseau.

Ce compte peut ne pas avoir accès au fichier de clé privée parce qu'il n'a pas installé le certificat à l'origine. L'outil FindPrivateKey vous donne l'emplacement du fichier de clé privée d'un certificat X.509 donné. Vous pouvez ajouter ou supprimer des autorisations à ce fichier une fois que vous connaissez l'emplacement du fichier de clé privée des certificats X.509 particuliers.

Les exemples qui utilisent des certificats pour la sécurité utilisent l’outil FindPrivateKey dans le fichier *Setup. bat* . Une fois le fichier de clé privée trouvé, vous pouvez utiliser d’autres outils tels que *cacls. exe* pour définir les droits d’accès appropriés sur le fichier.

Lors de l’exécution d’un service Windows Communication Foundation (WCF) sous un compte d’utilisateur, tel qu’un fichier exécutable auto-hébergé, vérifiez que le compte d’utilisateur dispose d’un accès en lecture seule au fichier. Lors de l’exécution d’un service WCF sous Internet Information Services (IIS), les comptes par défaut sous lesquels le service s’exécute sont le SERVICE réseau sur IIS 7 et les versions antérieures, ou l’identité du pool d’applications sur IIS 7,5 et versions ultérieures. Pour plus d’informations, consultez [identités du pool d’applications](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Exemples

Lorsque vous accédez à un certificat pour lequel le processus ne dispose pas de privilèges de lecture, un message d’exception semblable à l’exemple suivant s’affiche :

```output
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

Dans ce cas, utilisez l’outil FindPrivateKey pour rechercher le fichier de clé privée, puis définissez le droit d’accès pour le processus sous lequel le service s’exécute. Par exemple, cette opération peut être effectuée à l’aide de l’outil Cacls. exe, comme indiqué dans l’exemple suivant :

```console
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>Pour générer le projet FindPrivateKey

Pour télécharger le projet, visitez les [exemples Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

1. Ouvrez l’Explorateur de fichiers et accédez au dossier *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* sous l’emplacement du répertoire où vous avez installé l’exemple.

2. Double-cliquez sur l'icône du fichier .sln pour ouvrir ce dernier dans Visual Studio.

3. Dans le menu **générer** , sélectionnez **régénérer la solution**.

4. La génération de la solution génère le fichier : FindPrivateKey. exe.

## <a name="conventionscommand-line-entries"></a>Conventions-entrées de ligne de commande

 « [*option*] » représente un jeu facultatif de paramètres.

 « {*option*} » représente un ensemble obligatoire de paramètres.

 «*option1* &#124; *option2*» représente un choix entre des ensembles d’options.

 «\<*value*> » représente une valeur de paramètre à entrer.

## <a name="usage"></a>Usage

```console
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

Où :

| Paramètre         | Description                                                                       |
|-----------------|-----------------------------------------------------------------------------------|
| `<subjectName>` | Nom du sujet du certificat                                               |
| `<thumbprint>`  | Empreinte numérique du certificat (vous pouvez utiliser l’outil Certmgr. exe pour le Rechercher) |
| `-f`            | nom du fichier de sortie uniquement                                                             |
| `-d`            | Répertoire de sortie uniquement                                                             |
| `-a`            | nom de fichier absolu de sortie                                                         |

Si aucun paramètre n’est spécifié à l’invite de commandes, le texte d’aide avec ces informations s’affiche.

## <a name="examples"></a>Exemples

Cet exemple recherche le nom de fichier du certificat avec le nom de sujet « CN = localhost » dans le magasin personnel de l’utilisateur actuel.

```console
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Cet exemple recherche le nom de fichier du certificat avec le nom d’objet « CN = localhost » dans le magasin personnel de l’utilisateur actuel et génère le chemin d’accès complet au répertoire.

```console
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

Cet exemple recherche le nom de fichier du certificat avec l'empreinte numérique « 03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52 » dans le magasin personnel de l'ordinateur local.

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
