---
title: Exemple de FindPrivateKey - WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: b89d135d7412f10cb9de1e4bda1aaab14b29cbf0
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490774"
---
# <a name="findprivatekey-sample"></a>Exemple de FindPrivateKey

Il peut être difficile de rechercher l'emplacement et le nom du fichier de clé privée associé à un certificat X.509 spécifique dans le magasin de certificats. L'outil FindPrivateKey.exe facilite ce processus.

> [!IMPORTANT]
> FindPrivateKey est un exemple qui doit être compilé avant son utilisation. Consultez le [pour générer le projet FindPrivateKey](#to-build-the-findprivatekey-project) section pour obtenir des instructions sur la création de l’outil FindPrivateKey.

Les certificats X.509 sont installés par un administrateur ou tout utilisateur sur l'ordinateur. Toutefois, le certificat peut être consulté par un service en cours d’exécution sous un compte différent. Par exemple, le compte de SERVICE réseau.

Ce compte peut ne pas avoir accès au fichier de clé privée parce qu'il n'a pas installé le certificat à l'origine. L'outil FindPrivateKey vous donne l'emplacement du fichier de clé privée d'un certificat X.509 donné. Vous pouvez ajouter ou supprimer des autorisations à ce fichier une fois que vous connaissez l'emplacement du fichier de clé privée des certificats X.509 particuliers.

Les exemples qui utilisent des certificats pour la sécurité utilisent l’outil FindPrivateKey dans le *Setup.bat* fichier. Une fois que le fichier de clé privée a été trouvé, vous pouvez utiliser d’autres outils tels que *Cacls.exe* pour définir les droits d’accès appropriés sur le fichier.

Lors de l’exécution d’un service Windows Communication Foundation (WCF) sous un compte d’utilisateur, par exemple un fichier exécutable auto-hébergé, vérifiez que le compte d’utilisateur a accès en lecture seule au fichier. Lors de l’exécution d’un service WCF sous Internet Information Services (IIS) les comptes par défaut le service sous lequel s’exécute sont le SERVICE réseau sur IIS 7 et versions antérieures, ou identité de Pool d’applications sous IIS 7.5 et versions ultérieures. Pour plus d’informations, consultez [identités du Pool d’applications](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Exemples

Lorsque vous accédez à un certificat pour lequel le processus n’a pas les privilèges Lire, affiche un message d’exception semblable à l’exemple suivant :

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

Lorsque cela se produit, utilisez l’outil FindPrivateKey pour rechercher le fichier de clé privée, puis définissez le droit d’accès pour le processus que le service s’exécute sous. Par exemple, cela est possible avec l’outil Cacls.exe comme indiqué dans l’exemple suivant :

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>Pour générer le projet FindPrivateKey

Pour télécharger le projet, visitez [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

1. Ouvrez l’Explorateur de fichiers et accédez à la *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* dossier sous l’emplacement du répertoire où vous avez installé l’exemple.

2. Double-cliquez sur l'icône du fichier .sln pour ouvrir ce dernier dans Visual Studio.

3. Dans le **Build** menu, sélectionnez **régénérer la Solution**.

4. Génération de la solution génère le fichier : FindPrivateKey.exe.

## <a name="conventionscommand-line-entries"></a>Conventions, les entrées de ligne de commande

 « [*option*] » représente un jeu facultatif de paramètres.

 « {*option*} » représente un jeu obligatoire de paramètres.

 «*option1* &#124; *option2*» représente un choix entre plusieurs jeux d’options.

 «\<*valeur*> » représente une valeur de paramètre doit être entré.

## <a name="usage"></a>Utilisation

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

Où :

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

Si aucun paramètre est spécifié à l’invite de commande, ce texte d’aide s’affiche.

## <a name="examples"></a>Exemples

Cet exemple recherche le nom de fichier du certificat avec le nom de sujet « CN = localhost », dans le magasin personnel de l’utilisateur actuel.

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Cet exemple recherche le nom de fichier du certificat avec le nom de sujet « CN = localhost », dans le profil personnel et stocker de l’utilisateur actuel et le chemin d’accès complet du répertoire de sortie.

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

Cet exemple recherche le nom de fichier du certificat avec l'empreinte numérique « 03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52 » dans le magasin personnel de l'ordinateur local.

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
