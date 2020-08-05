---
title: 'Procédure pas à pas : création d’une application de chiffrement'
description: Parcourez la création d’une application de chiffrement. Découvrez comment chiffrer et déchiffrer le contenu d’une application Windows Forms.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET], example
- cryptography [NET], cryptographic application example
- cryptography [NET], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
ms.openlocfilehash: 16a887f23c584daa83106ae61c497bcae8dc4dd2
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557188"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a>Procédure pas à pas : création d’une application de chiffrement

> [!NOTE]
> Cet article s’applique à Windows.
>
> Pour plus d’informations sur la ASP.NET Core, consultez [protection des données ASP.net Core](/aspnet/core/security/data-protection/introduction).

Cette procédure pas à pas montre comment chiffrer et déchiffrer du contenu. Les exemples de code sont conçus pour une application Windows Forms. Cette application ne montre pas de scénarios du monde réel, tels que l'utilisation de cartes à puce. Elle montre les principes fondamentaux du chiffrement et du déchiffrement.  
  
Cette procédure pas à pas utilise les indications suivantes pour le chiffrement :  
  
- Utilisez <xref:System.Security.Cryptography.Aes> (algorithme symétrique) pour chiffrer et déchiffrer des données à l'aide des <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> et <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> générés automatiquement.  
  
- Utilisez l' <xref:System.Security.Cryptography.RSA> algorithme asymétrique pour chiffrer et déchiffrer la clé aux données chiffrées par <xref:System.Security.Cryptography.Aes> . Il est préférable d'utiliser les algorithmes asymétriques pour les petites quantités de données, telles qu'une clé.  
  
    > [!NOTE]
    > Si vous souhaitez protéger les données sur votre ordinateur au lieu d’échanger du contenu chiffré avec d’autres personnes, envisagez d’utiliser la <xref:System.Security.Cryptography.ProtectedData> classe.  
  
 Le tableau suivant récapitule les tâches de chiffrement de cette rubrique.  
  
|Tâche|Description|  
|----------|-----------------|  
|Création d'une application Windows Forms|Répertorie les contrôles qui sont nécessaires pour exécuter l'application.|  
|Déclaration d'objets globaux|Déclare les variables de chemin de chaîne, <xref:System.Security.Cryptography.CspParameters> et <xref:System.Security.Cryptography.RSACryptoServiceProvider>, pour obtenir le contexte global de la classe <xref:System.Windows.Forms.Form>.|  
|Création d'une clé asymétrique|Crée une paire de valeurs de clés publique et privée asymétriques, et lui assigne un nom de conteneur de clé.|  
|Chiffrement d'un fichier|Affiche une boîte de dialogue pour sélectionner un fichier à chiffrer, puis chiffre le fichier.|  
|Déchiffrement d'un fichier|Affiche une boîte de dialogue pour sélectionner un fichier à déchiffrer, puis déchiffre le fichier.|  
|Obtention d'une clé privée|Obtient la paire de clés complète en utilisant le nom du conteneur de clé.|  
|Exportation d'une clé publique|Enregistre la clé dans un fichier XML avec uniquement les paramètres publics.|  
|Importation d'une clé publique|Charge la clé d'un fichier XML dans le conteneur de clé.|  
|Test de l’application|Répertorie les procédures pour le test de cette application.|  
  
## <a name="prerequisites"></a>Prérequis  

Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :  
  
- Références aux espaces de noms <xref:System.IO> et <xref:System.Security.Cryptography>.  
  
## <a name="creating-a-windows-forms-application"></a>Création d’une application Windows Forms  

La plupart des exemples de code de cette procédure pas à pas sont conçus pour être des gestionnaires d'événements pour des contrôles de bouton. Le tableau suivant répertorie les contrôles requis par l'exemple d'application, ainsi que leur nom pour correspondre aux exemples de code.  
  
|Control|Nom|Propriété Text (si nécessaire)|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|Chiffrer le fichier|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|Déchiffrer le fichier|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|Créer des clés|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|Exporter une clé publique|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|Importer une clé publique|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|Obtenir une clé privée|  
|<xref:System.Windows.Forms.Label>|`label1`|Clé non définie|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 Double-cliquez sur les boutons dans le concepteur Visual Studio pour créer leurs gestionnaires d’événements.
  
## <a name="declaring-global-objects"></a>Déclaration d'objets globaux  

Ajoutez le code suivant au constructeur du formulaire : Modifiez les variables de chaîne pour votre environnement et vos préférences.  
  
[!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
[!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a>Création d'une clé asymétrique  

Cette tâche crée une clé asymétrique qui chiffre et déchiffre la clé <xref:System.Security.Cryptography.Aes>. Cette clé a été utilisée pour chiffrer le contenu et elle affiche le nom du conteneur de clé sur le contrôle d'étiquette.  
  
 Ajoutez le code suivant en tant que gestionnaire d'événements `Click` pour le bouton `Create Keys` (`buttonCreateAsmKeys_Click`).  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a>Chiffrement d'un fichier  

Cette tâche implique deux méthodes : la méthode de gestionnaire d’événements pour le `Encrypt File` bouton ( `buttonEncryptFile_Click` ) et la `EncryptFile` méthode. La première méthode affiche une boîte de dialogue permettant de sélectionner un fichier, puis passe le nom du fichier à la deuxième méthode qui effectue le chiffrement.  
  
Le contenu chiffré, la clé et le vecteur d'initialisation sont enregistrés dans un <xref:System.IO.FileStream>, qui correspond au package de chiffrement.  
  
La méthode `EncryptFile` effectue les opérations suivantes :  
  
1. Elle crée un algorithme symétrique <xref:System.Security.Cryptography.Aes> pour chiffrer le contenu.  
  
2. Elle crée un objet <xref:System.Security.Cryptography.RSACryptoServiceProvider> pour chiffrer la clé <xref:System.Security.Cryptography.Aes>.  
  
3. Elle utilise un objet <xref:System.Security.Cryptography.CryptoStream> pour lire et chiffrer le <xref:System.IO.FileStream> du fichier source (par blocs d'octets) dans un objet <xref:System.IO.FileStream> de destination pour le fichier chiffré.  
  
4. Détermine la longueur de la clé chiffrée et du vecteur d'initialisation, puis crée des tableaux d'octets à partir de leurs valeurs de longueur.  
  
5. Écrit la clé, le vecteur d'initialisation et leurs valeurs de longueur dans le package chiffré.  
  
 Le package chiffré utilise le format suivant :  
  
- Longueur de la clé, octets 0-3  
  
- Longueur du vecteur d'initialisation, octets 4-7  
  
- Clé chiffrée  
  
- IV  
  
- Texte chiffré  
  
 Vous pouvez utiliser la longueur de la clé et du vecteur d'initialisation pour déterminer les points de départ et les longueurs de tous les composants du package chiffré, qui peuvent ensuite être utilisés pour déchiffrer le fichier.  
  
 Ajoutez le code suivant en tant que gestionnaire d'événements `Click` pour le bouton `Encrypt File` (`buttonEncryptFile_Click`).  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 Ajoutez la méthode `EncryptFile` suivante au formulaire :  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a>Déchiffrement d'un fichier  

Cette tâche inclut deux méthodes : la méthode de gestionnaire d’événements pour le bouton `Decrypt File` (`buttonDecryptFile_Click`) et la méthode `DecryptFile`. La première méthode affiche une boîte de dialogue permettant de sélectionner un fichier, puis passe le nom du fichier à la deuxième méthode qui effectue le déchiffrement.  
  
La méthode `Decrypt` effectue les opérations suivantes :  
  
1. Crée un <xref:System.Security.Cryptography.Aes> algorithme symétrique pour déchiffrer le contenu.  
  
2. Elle lit les huit premiers octets du <xref:System.IO.FileStream> du package chiffré dans les tableaux d'octets pour obtenir la longueur de la clé et du vecteur d'initialisation.  
  
3. Elle extrait la clé et le vecteur d'initialisation du package de chiffrement dans des tableaux d'octets.  
  
4. Elle crée un objet <xref:System.Security.Cryptography.RSACryptoServiceProvider> pour déchiffrer la clé <xref:System.Security.Cryptography.Aes>.  
  
5. Elle utilise un objet <xref:System.Security.Cryptography.CryptoStream> pour lire et déchiffrer la section de texte chiffré du package de chiffrement <xref:System.IO.FileStream> (par blocs d'octets) dans l'objet <xref:System.IO.FileStream> pour le fichier déchiffré. Quand cette étape est terminée, le déchiffrement est terminé.  
  
 Ajoutez le code suivant en tant que gestionnaire d'événements `Click` pour le bouton `Decrypt File`.  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 Ajoutez la méthode `DecryptFile` suivante au formulaire :  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a>Exportation d'une clé publique

Cette tâche enregistre la clé créée par le bouton `Create Keys` dans un fichier. Elle exporte uniquement les paramètres publics.  
  
Cette tâche décrit le scénario dans lequel Alice confie à Bob sa clé publique pour qu’il puisse chiffrer des fichiers pour elle. Bob et les autres utilisateurs de cette clé publique ne pourront pas les déchiffrer, car ils ne disposent pas de la paire de clés complète avec les paramètres privés.  
  
Ajoutez le code suivant en tant que gestionnaire d'événements `Click` pour le bouton `Export Public Key` (`buttonExportPublicKey_Click`).  
  
[!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
[!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a>Importation d'une clé publique

Cette tâche charge la clé avec les paramètres publics uniquement, tels que créés par le bouton `Export Public Key`, et la définit comme le nom du conteneur de clé.  
  
Cette tâche simule le scénario dans lequel Bob charge la clé d’Alice avec les paramètres publics uniquement pour chiffrer ses fichiers.  
  
Ajoutez le code suivant en tant que gestionnaire d'événements `Click` pour le bouton `Import Public Key` (`buttonImportPublicKey_Click`).  
  
[!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
[!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a>Obtention d'une clé privée  

Cette tâche définit le nom du conteneur de clé sur le nom de la clé créée à l'aide du bouton `Create Keys`. Le conteneur de clé contiendra la paire de clés complète avec les paramètres privés.  
  
Cette tâche simule le scénario dans lequel Alice utilise sa clé privée pour déchiffrer les fichiers chiffrés par Bob.  
  
Ajoutez le code suivant en tant que gestionnaire d'événements `Click` pour le bouton `Get Private Key` (`buttonGetPrivateKey_Click`).  
  
[!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
[!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a>Test de l’application

Après avoir créé l'application, suivez les scénarios de test ci-dessous.  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a>Pour créer, chiffrer et déchiffrer des clés  
  
1. Cliquez sur le bouton `Create Keys`. L'étiquette affiche le nom de la clé et montre qu'il s'agit d'une paire de clés complète.  
  
2. Cliquez sur le bouton `Export Public Key`. Notez que l'exportation des paramètres de la clé publique ne modifie pas la clé actuelle.  
  
3. Cliquez sur le bouton `Encrypt File`, puis sélectionnez un fichier.  
  
4. Cliquez sur le bouton `Decrypt File`, puis sélectionnez le fichier chiffré.  
  
5. Examinez le fichier déchiffré.  
  
6. Fermez l'application, puis redémarrez-la pour tester la récupération des conteneurs de clé persistants dans le scénario suivant.  
  
#### <a name="to-encrypt-using-the-public-key"></a>Pour chiffrer à l'aide de la clé publique  
  
1. Cliquez sur le bouton `Import Public Key`. L'étiquette affiche le nom de la clé et montre qu'il s'agit d'une clé publique uniquement.  
  
2. Cliquez sur le bouton `Encrypt File`, puis sélectionnez un fichier.  
  
3. Cliquez sur le bouton `Decrypt File`, puis sélectionnez le fichier chiffré. Le processus échouera, car vous devez disposer de la clé privée pour effectuer le déchiffrement.  
  
 Dans ce scénario, un utilisateur dispose uniquement de la clé publique pour chiffrer le fichier d'un autre utilisateur. En général, l'utilisateur donne uniquement la clé publique et conserve la clé privée pour le déchiffrement.  
  
#### <a name="to-decrypt-using-the-private-key"></a>Pour déchiffrer à l'aide de la clé privée  
  
1. Cliquez sur le bouton `Get Private Key`. L'étiquette affiche le nom de la clé et montre s'il s'agit d'une paire de clés complète.  
  
2. Cliquez sur le bouton `Decrypt File`, puis sélectionnez le fichier chiffré. Cette opération réussira, car vous disposez de la paire de clés complète pour le déchiffrement.  
  
## <a name="see-also"></a>Voir aussi

- [Modèle de chiffrement](cryptography-model.md) -décrit comment le chiffrement est implémenté dans la bibliothèque de classes de base.
- [services de chiffrement](cryptographic-services.md)
- [Chiffrement multiplateforme](cross-platform-cryptography.md)
- [Protection des données ASP.NET Core](/aspnet/core/security/data-protection/introduction)
