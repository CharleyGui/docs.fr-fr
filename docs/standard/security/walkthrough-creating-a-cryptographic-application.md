---
title: "Procédure pas à pas : création d'une application de chiffrement"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
ms.openlocfilehash: 246028566c59e5c8a77b26a21729d3f143d38d07
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289705"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="5be7f-102">Procédure pas à pas : création d'une application de chiffrement</span><span class="sxs-lookup"><span data-stu-id="5be7f-102">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="5be7f-103">Cette procédure pas à pas montre comment chiffrer et déchiffrer du contenu.</span><span class="sxs-lookup"><span data-stu-id="5be7f-103">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="5be7f-104">Les exemples de code sont conçus pour une application Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5be7f-104">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="5be7f-105">Cette application ne montre pas de scénarios du monde réel, tels que l'utilisation de cartes à puce.</span><span class="sxs-lookup"><span data-stu-id="5be7f-105">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="5be7f-106">Elle montre les principes fondamentaux du chiffrement et du déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="5be7f-106">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="5be7f-107">Cette procédure pas à pas utilise les indications suivantes pour le chiffrement :</span><span class="sxs-lookup"><span data-stu-id="5be7f-107">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="5be7f-108">Utilisez <xref:System.Security.Cryptography.RijndaelManaged> (algorithme symétrique) pour chiffrer et déchiffrer des données à l'aide des <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> et <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> générés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="5be7f-108">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="5be7f-109">Utilisez <xref:System.Security.Cryptography.RSACryptoServiceProvider> (algorithme asymétrique) pour chiffrer et déchiffrer la clé des données chiffrées par <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="5be7f-109">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="5be7f-110">Il est préférable d'utiliser les algorithmes asymétriques pour les petites quantités de données, telles qu'une clé.</span><span class="sxs-lookup"><span data-stu-id="5be7f-110">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5be7f-111">Si vous voulez protéger les données de votre ordinateur au lieu d'échanger du contenu chiffré avec d'autres personnes, envisagez d'utiliser les classes <xref:System.Security.Cryptography.ProtectedData> et <xref:System.Security.Cryptography.ProtectedMemory>.</span><span class="sxs-lookup"><span data-stu-id="5be7f-111">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="5be7f-112">Le tableau suivant récapitule les tâches de chiffrement de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="5be7f-112">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="5be7f-113">Tâche</span><span class="sxs-lookup"><span data-stu-id="5be7f-113">Task</span></span>|<span data-ttu-id="5be7f-114">Description</span><span class="sxs-lookup"><span data-stu-id="5be7f-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="5be7f-115">Création d'une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5be7f-115">Creating a Windows Forms application</span></span>|<span data-ttu-id="5be7f-116">Répertorie les contrôles qui sont nécessaires pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="5be7f-116">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="5be7f-117">Déclaration d'objets globaux</span><span class="sxs-lookup"><span data-stu-id="5be7f-117">Declaring global objects</span></span>|<span data-ttu-id="5be7f-118">Déclare les variables de chemin de chaîne, <xref:System.Security.Cryptography.CspParameters> et <xref:System.Security.Cryptography.RSACryptoServiceProvider>, pour obtenir le contexte global de la classe <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="5be7f-118">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="5be7f-119">Création d'une clé asymétrique</span><span class="sxs-lookup"><span data-stu-id="5be7f-119">Creating an asymmetric key</span></span>|<span data-ttu-id="5be7f-120">Crée une paire de valeurs de clés publique et privée asymétriques, et lui assigne un nom de conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="5be7f-120">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="5be7f-121">Chiffrement d'un fichier</span><span class="sxs-lookup"><span data-stu-id="5be7f-121">Encrypting a file</span></span>|<span data-ttu-id="5be7f-122">Affiche une boîte de dialogue pour sélectionner un fichier à chiffrer, puis chiffre le fichier.</span><span class="sxs-lookup"><span data-stu-id="5be7f-122">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="5be7f-123">Déchiffrement d'un fichier</span><span class="sxs-lookup"><span data-stu-id="5be7f-123">Decrypting a file</span></span>|<span data-ttu-id="5be7f-124">Affiche une boîte de dialogue pour sélectionner un fichier à déchiffrer, puis déchiffre le fichier.</span><span class="sxs-lookup"><span data-stu-id="5be7f-124">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="5be7f-125">Obtention d'une clé privée</span><span class="sxs-lookup"><span data-stu-id="5be7f-125">Getting a private key</span></span>|<span data-ttu-id="5be7f-126">Obtient la paire de clés complète en utilisant le nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="5be7f-126">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="5be7f-127">Exportation d'une clé publique</span><span class="sxs-lookup"><span data-stu-id="5be7f-127">Exporting a public key</span></span>|<span data-ttu-id="5be7f-128">Enregistre la clé dans un fichier XML avec uniquement les paramètres publics.</span><span class="sxs-lookup"><span data-stu-id="5be7f-128">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="5be7f-129">Importation d'une clé publique</span><span class="sxs-lookup"><span data-stu-id="5be7f-129">Importing a public key</span></span>|<span data-ttu-id="5be7f-130">Charge la clé d'un fichier XML dans le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="5be7f-130">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="5be7f-131">Test de l’application</span><span class="sxs-lookup"><span data-stu-id="5be7f-131">Testing the application</span></span>|<span data-ttu-id="5be7f-132">Répertorie les procédures pour le test de cette application.</span><span class="sxs-lookup"><span data-stu-id="5be7f-132">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="5be7f-133">Prérequis</span><span class="sxs-lookup"><span data-stu-id="5be7f-133">Prerequisites</span></span>  
 <span data-ttu-id="5be7f-134">Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :</span><span class="sxs-lookup"><span data-stu-id="5be7f-134">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="5be7f-135">Références aux espaces de noms <xref:System.IO> et <xref:System.Security.Cryptography>.</span><span class="sxs-lookup"><span data-stu-id="5be7f-135">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="5be7f-136">Création d’une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5be7f-136">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="5be7f-137">La plupart des exemples de code de cette procédure pas à pas sont conçus pour être des gestionnaires d'événements pour des contrôles de bouton.</span><span class="sxs-lookup"><span data-stu-id="5be7f-137">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="5be7f-138">Le tableau suivant répertorie les contrôles requis par l'exemple d'application, ainsi que leur nom pour correspondre aux exemples de code.</span><span class="sxs-lookup"><span data-stu-id="5be7f-138">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="5be7f-139">Control</span><span class="sxs-lookup"><span data-stu-id="5be7f-139">Control</span></span>|<span data-ttu-id="5be7f-140">Nom</span><span class="sxs-lookup"><span data-stu-id="5be7f-140">Name</span></span>|<span data-ttu-id="5be7f-141">Propriété Text (si nécessaire)</span><span class="sxs-lookup"><span data-stu-id="5be7f-141">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="5be7f-142">Chiffrer le fichier</span><span class="sxs-lookup"><span data-stu-id="5be7f-142">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="5be7f-143">Déchiffrer le fichier</span><span class="sxs-lookup"><span data-stu-id="5be7f-143">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="5be7f-144">Créer des clés</span><span class="sxs-lookup"><span data-stu-id="5be7f-144">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="5be7f-145">Exporter une clé publique</span><span class="sxs-lookup"><span data-stu-id="5be7f-145">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="5be7f-146">Importer une clé publique</span><span class="sxs-lookup"><span data-stu-id="5be7f-146">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="5be7f-147">Obtenir une clé privée</span><span class="sxs-lookup"><span data-stu-id="5be7f-147">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="5be7f-148">Clé non définie</span><span class="sxs-lookup"><span data-stu-id="5be7f-148">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="5be7f-149">Double-cliquez sur les boutons de Visual Studio Designer pour créer leurs gestionnaires d'événements.</span><span class="sxs-lookup"><span data-stu-id="5be7f-149">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="5be7f-150">Déclaration d'objets globaux</span><span class="sxs-lookup"><span data-stu-id="5be7f-150">Declaring Global Objects</span></span>  
 <span data-ttu-id="5be7f-151">Ajoutez le code suivant au constructeur du formulaire :</span><span class="sxs-lookup"><span data-stu-id="5be7f-151">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="5be7f-152">Modifiez les variables de chaîne pour votre environnement et vos préférences.</span><span class="sxs-lookup"><span data-stu-id="5be7f-152">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="5be7f-153">Création d'une clé asymétrique</span><span class="sxs-lookup"><span data-stu-id="5be7f-153">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="5be7f-154">Cette tâche crée une clé asymétrique qui chiffre et déchiffre la clé <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="5be7f-154">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="5be7f-155">Cette clé a été utilisée pour chiffrer le contenu et elle affiche le nom du conteneur de clé sur le contrôle d'étiquette.</span><span class="sxs-lookup"><span data-stu-id="5be7f-155">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="5be7f-156">Ajoutez le code suivant en tant que gestionnaire d'événements `Click` pour le bouton `Create Keys` (`buttonCreateAsmKeys_Click`).</span><span class="sxs-lookup"><span data-stu-id="5be7f-156">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="5be7f-157">Chiffrement d'un fichier</span><span class="sxs-lookup"><span data-stu-id="5be7f-157">Encrypting a File</span></span>  
 <span data-ttu-id="5be7f-158">Cette tâche implique deux méthodes : la méthode de gestionnaire d’événements pour le `Encrypt File` bouton ( `buttonEncryptFile_Click` ) et la `EncryptFile` méthode.</span><span class="sxs-lookup"><span data-stu-id="5be7f-158">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="5be7f-159">La première méthode affiche une boîte de dialogue permettant de sélectionner un fichier, puis passe le nom du fichier à la deuxième méthode qui effectue le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="5be7f-159">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="5be7f-160">Le contenu chiffré, la clé et le vecteur d'initialisation sont enregistrés dans un <xref:System.IO.FileStream>, qui correspond au package de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="5be7f-160">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="5be7f-161">La méthode `EncryptFile` effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5be7f-161">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="5be7f-162">Elle crée un algorithme symétrique <xref:System.Security.Cryptography.RijndaelManaged> pour chiffrer le contenu.</span><span class="sxs-lookup"><span data-stu-id="5be7f-162">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="5be7f-163">Elle crée un objet <xref:System.Security.Cryptography.RSACryptoServiceProvider> pour chiffrer la clé <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="5be7f-163">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3. <span data-ttu-id="5be7f-164">Elle utilise un objet <xref:System.Security.Cryptography.CryptoStream> pour lire et chiffrer le <xref:System.IO.FileStream> du fichier source (par blocs d'octets) dans un objet <xref:System.IO.FileStream> de destination pour le fichier chiffré.</span><span class="sxs-lookup"><span data-stu-id="5be7f-164">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="5be7f-165">Détermine la longueur de la clé chiffrée et du vecteur d'initialisation, puis crée des tableaux d'octets à partir de leurs valeurs de longueur.</span><span class="sxs-lookup"><span data-stu-id="5be7f-165">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="5be7f-166">Écrit la clé, le vecteur d'initialisation et leurs valeurs de longueur dans le package chiffré.</span><span class="sxs-lookup"><span data-stu-id="5be7f-166">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="5be7f-167">Le package chiffré utilise le format suivant :</span><span class="sxs-lookup"><span data-stu-id="5be7f-167">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="5be7f-168">Longueur de la clé, octets 0-3</span><span class="sxs-lookup"><span data-stu-id="5be7f-168">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="5be7f-169">Longueur du vecteur d'initialisation, octets 4-7</span><span class="sxs-lookup"><span data-stu-id="5be7f-169">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="5be7f-170">Clé chiffrée</span><span class="sxs-lookup"><span data-stu-id="5be7f-170">Encrypted key</span></span>  
  
- <span data-ttu-id="5be7f-171">IV</span><span class="sxs-lookup"><span data-stu-id="5be7f-171">IV</span></span>  
  
- <span data-ttu-id="5be7f-172">Texte chiffré</span><span class="sxs-lookup"><span data-stu-id="5be7f-172">Cipher text</span></span>  
  
 <span data-ttu-id="5be7f-173">Vous pouvez utiliser la longueur de la clé et du vecteur d'initialisation pour déterminer les points de départ et les longueurs de tous les composants du package chiffré, qui peuvent ensuite être utilisés pour déchiffrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="5be7f-173">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="5be7f-174">Ajoutez le code suivant en tant que gestionnaire d'événements `Click` pour le bouton `Encrypt File` (`buttonEncryptFile_Click`).</span><span class="sxs-lookup"><span data-stu-id="5be7f-174">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="5be7f-175">Ajoutez la méthode `EncryptFile` suivante au formulaire :</span><span class="sxs-lookup"><span data-stu-id="5be7f-175">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="5be7f-176">Déchiffrement d'un fichier</span><span class="sxs-lookup"><span data-stu-id="5be7f-176">Decrypting a File</span></span>  
 <span data-ttu-id="5be7f-177">Cette tâche inclut deux méthodes : la méthode de gestionnaire d’événements pour le bouton `Decrypt File` (`buttonDecryptFile_Click`) et la méthode `DecryptFile`.</span><span class="sxs-lookup"><span data-stu-id="5be7f-177">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="5be7f-178">La première méthode affiche une boîte de dialogue permettant de sélectionner un fichier, puis passe le nom du fichier à la deuxième méthode qui effectue le déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="5be7f-178">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="5be7f-179">La méthode `Decrypt` effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5be7f-179">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="5be7f-180">Elle crée un algorithme symétrique <xref:System.Security.Cryptography.RijndaelManaged> pour déchiffrer le contenu.</span><span class="sxs-lookup"><span data-stu-id="5be7f-180">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="5be7f-181">Elle lit les huit premiers octets du <xref:System.IO.FileStream> du package chiffré dans les tableaux d'octets pour obtenir la longueur de la clé et du vecteur d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="5be7f-181">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="5be7f-182">Elle extrait la clé et le vecteur d'initialisation du package de chiffrement dans des tableaux d'octets.</span><span class="sxs-lookup"><span data-stu-id="5be7f-182">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="5be7f-183">Elle crée un objet <xref:System.Security.Cryptography.RSACryptoServiceProvider> pour déchiffrer la clé <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="5be7f-183">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5. <span data-ttu-id="5be7f-184">Elle utilise un objet <xref:System.Security.Cryptography.CryptoStream> pour lire et déchiffrer la section de texte chiffré du package de chiffrement <xref:System.IO.FileStream> (par blocs d'octets) dans l'objet <xref:System.IO.FileStream> pour le fichier déchiffré.</span><span class="sxs-lookup"><span data-stu-id="5be7f-184">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="5be7f-185">Quand cette étape est terminée, le déchiffrement est terminé.</span><span class="sxs-lookup"><span data-stu-id="5be7f-185">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="5be7f-186">Ajoutez le code suivant en tant que gestionnaire d'événements `Click` pour le bouton `Decrypt File`.</span><span class="sxs-lookup"><span data-stu-id="5be7f-186">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="5be7f-187">Ajoutez la méthode `DecryptFile` suivante au formulaire :</span><span class="sxs-lookup"><span data-stu-id="5be7f-187">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="5be7f-188">Exportation d'une clé publique</span><span class="sxs-lookup"><span data-stu-id="5be7f-188">Exporting a Public Key</span></span>  
 <span data-ttu-id="5be7f-189">Cette tâche enregistre la clé créée par le bouton `Create Keys` dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="5be7f-189">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="5be7f-190">Elle exporte uniquement les paramètres publics.</span><span class="sxs-lookup"><span data-stu-id="5be7f-190">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="5be7f-191">Cette tâche décrit le scénario dans lequel Alice confie à Bob sa clé publique pour qu’il puisse chiffrer des fichiers pour elle.</span><span class="sxs-lookup"><span data-stu-id="5be7f-191">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="5be7f-192">Bob et les autres utilisateurs de cette clé publique ne pourront pas les déchiffrer, car ils ne disposent pas de la paire de clés complète avec les paramètres privés.</span><span class="sxs-lookup"><span data-stu-id="5be7f-192">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="5be7f-193">Ajoutez le code suivant en tant que gestionnaire d'événements `Click` pour le bouton `Export Public Key` (`buttonExportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="5be7f-193">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="5be7f-194">Importation d'une clé publique</span><span class="sxs-lookup"><span data-stu-id="5be7f-194">Importing a Public Key</span></span>  
 <span data-ttu-id="5be7f-195">Cette tâche charge la clé avec les paramètres publics uniquement, tels que créés par le bouton `Export Public Key`, et la définit comme le nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="5be7f-195">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="5be7f-196">Cette tâche simule le scénario dans lequel Bob charge la clé d’Alice avec les paramètres publics uniquement pour chiffrer ses fichiers.</span><span class="sxs-lookup"><span data-stu-id="5be7f-196">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="5be7f-197">Ajoutez le code suivant en tant que gestionnaire d'événements `Click` pour le bouton `Import Public Key` (`buttonImportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="5be7f-197">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="5be7f-198">Obtention d'une clé privée</span><span class="sxs-lookup"><span data-stu-id="5be7f-198">Getting a Private Key</span></span>  
 <span data-ttu-id="5be7f-199">Cette tâche définit le nom du conteneur de clé sur le nom de la clé créée à l'aide du bouton `Create Keys`.</span><span class="sxs-lookup"><span data-stu-id="5be7f-199">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="5be7f-200">Le conteneur de clé contiendra la paire de clés complète avec les paramètres privés.</span><span class="sxs-lookup"><span data-stu-id="5be7f-200">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="5be7f-201">Cette tâche simule le scénario dans lequel Alice utilise sa clé privée pour déchiffrer les fichiers chiffrés par Bob.</span><span class="sxs-lookup"><span data-stu-id="5be7f-201">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="5be7f-202">Ajoutez le code suivant en tant que gestionnaire d'événements `Click` pour le bouton `Get Private Key` (`buttonGetPrivateKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="5be7f-202">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="5be7f-203">Test de l’application</span><span class="sxs-lookup"><span data-stu-id="5be7f-203">Testing the Application</span></span>  
 <span data-ttu-id="5be7f-204">Après avoir créé l'application, suivez les scénarios de test ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="5be7f-204">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="5be7f-205">Pour créer, chiffrer et déchiffrer des clés</span><span class="sxs-lookup"><span data-stu-id="5be7f-205">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="5be7f-206">Cliquez sur le bouton `Create Keys`.</span><span class="sxs-lookup"><span data-stu-id="5be7f-206">Click the `Create Keys` button.</span></span> <span data-ttu-id="5be7f-207">L'étiquette affiche le nom de la clé et montre qu'il s'agit d'une paire de clés complète.</span><span class="sxs-lookup"><span data-stu-id="5be7f-207">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="5be7f-208">Cliquez sur le bouton `Export Public Key`.</span><span class="sxs-lookup"><span data-stu-id="5be7f-208">Click the `Export Public Key` button.</span></span> <span data-ttu-id="5be7f-209">Notez que l'exportation des paramètres de la clé publique ne modifie pas la clé actuelle.</span><span class="sxs-lookup"><span data-stu-id="5be7f-209">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="5be7f-210">Cliquez sur le bouton `Encrypt File`, puis sélectionnez un fichier.</span><span class="sxs-lookup"><span data-stu-id="5be7f-210">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="5be7f-211">Cliquez sur le bouton `Decrypt File`, puis sélectionnez le fichier chiffré.</span><span class="sxs-lookup"><span data-stu-id="5be7f-211">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="5be7f-212">Examinez le fichier déchiffré.</span><span class="sxs-lookup"><span data-stu-id="5be7f-212">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="5be7f-213">Fermez l'application, puis redémarrez-la pour tester la récupération des conteneurs de clé persistants dans le scénario suivant.</span><span class="sxs-lookup"><span data-stu-id="5be7f-213">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="5be7f-214">Pour chiffrer à l'aide de la clé publique</span><span class="sxs-lookup"><span data-stu-id="5be7f-214">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="5be7f-215">Cliquez sur le bouton `Import Public Key`.</span><span class="sxs-lookup"><span data-stu-id="5be7f-215">Click the `Import Public Key` button.</span></span> <span data-ttu-id="5be7f-216">L'étiquette affiche le nom de la clé et montre qu'il s'agit d'une clé publique uniquement.</span><span class="sxs-lookup"><span data-stu-id="5be7f-216">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="5be7f-217">Cliquez sur le bouton `Encrypt File`, puis sélectionnez un fichier.</span><span class="sxs-lookup"><span data-stu-id="5be7f-217">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="5be7f-218">Cliquez sur le bouton `Decrypt File`, puis sélectionnez le fichier chiffré.</span><span class="sxs-lookup"><span data-stu-id="5be7f-218">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="5be7f-219">Le processus échouera, car vous devez disposer de la clé privée pour effectuer le déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="5be7f-219">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="5be7f-220">Dans ce scénario, un utilisateur dispose uniquement de la clé publique pour chiffrer le fichier d'un autre utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5be7f-220">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="5be7f-221">En général, l'utilisateur donne uniquement la clé publique et conserve la clé privée pour le déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="5be7f-221">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="5be7f-222">Pour déchiffrer à l'aide de la clé privée</span><span class="sxs-lookup"><span data-stu-id="5be7f-222">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="5be7f-223">Cliquez sur le bouton `Get Private Key`.</span><span class="sxs-lookup"><span data-stu-id="5be7f-223">Click the `Get Private Key` button.</span></span> <span data-ttu-id="5be7f-224">L'étiquette affiche le nom de la clé et montre s'il s'agit d'une paire de clés complète.</span><span class="sxs-lookup"><span data-stu-id="5be7f-224">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="5be7f-225">Cliquez sur le bouton `Decrypt File`, puis sélectionnez le fichier chiffré.</span><span class="sxs-lookup"><span data-stu-id="5be7f-225">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="5be7f-226">Cette opération réussira, car vous disposez de la paire de clés complète pour le déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="5be7f-226">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5be7f-227">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5be7f-227">See also</span></span>

- [<span data-ttu-id="5be7f-228">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="5be7f-228">Cryptographic Services</span></span>](cryptographic-services.md)
