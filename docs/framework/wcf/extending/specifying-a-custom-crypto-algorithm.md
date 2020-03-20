---
title: Spécification d'un algorithme de chiffrement personnalisé
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 673d177a665e265d77f0221e0a00f4b814c8795c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186490"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="69d23-102">Spécification d'un algorithme de chiffrement personnalisé</span><span class="sxs-lookup"><span data-stu-id="69d23-102">Specifying a Custom Crypto Algorithm</span></span>
<span data-ttu-id="69d23-103">WCF vous permet de spécifier un algorithme de chiffrement personnalité pour le chiffrement des données ou le calcul de signatures numériques.</span><span class="sxs-lookup"><span data-stu-id="69d23-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="69d23-104">Voici les étapes qui permettent d'effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="69d23-104">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="69d23-105">Dériver une classe de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span><span class="sxs-lookup"><span data-stu-id="69d23-105">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="69d23-106">Enregistrer l'algorithme</span><span class="sxs-lookup"><span data-stu-id="69d23-106">Register the algorithm</span></span>  
  
3. <span data-ttu-id="69d23-107">Configurez la liaison avec la classe dérivée <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="69d23-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="69d23-108">Dériver une classe de SecurityAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="69d23-108">Derive a class from SecurityAlgorithmSuite</span></span>  
 <span data-ttu-id="69d23-109">La classe <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> est une classe de base abstraite qui vous permet de spécifier l'algorithme à utiliser pour plusieurs opérations liées à la sécurité.</span><span class="sxs-lookup"><span data-stu-id="69d23-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="69d23-110">Par exemple, calculer un hachage pour une signature numérique ou chiffrer un message.</span><span class="sxs-lookup"><span data-stu-id="69d23-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="69d23-111">Le code suivant montre comment dériver une classe à partir de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> :</span><span class="sxs-lookup"><span data-stu-id="69d23-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="69d23-112">Enregistrer l'algorithme personnalisé</span><span class="sxs-lookup"><span data-stu-id="69d23-112">Register the Custom Algorithm</span></span>  
 <span data-ttu-id="69d23-113">L'enregistrement peut être effectué dans un fichier de configuration ou en code impératif.</span><span class="sxs-lookup"><span data-stu-id="69d23-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="69d23-114">L'enregistrement d'un algorithme personnalisé s'effectue en créant un mappage entre une classe qui implémente un fournisseur de service de chiffrement et un alias.</span><span class="sxs-lookup"><span data-stu-id="69d23-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="69d23-115">L’alias est ensuite mappé sur un URI qui est utilisé pour spécifier l’algorithme dans la liaison du service WCF.</span><span class="sxs-lookup"><span data-stu-id="69d23-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="69d23-116">L'extrait de configuration suivant illustre la méthode d'enregistrement d'un algorithme personnalisé :</span><span class="sxs-lookup"><span data-stu-id="69d23-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://constoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="69d23-117">La section sous l’élément `cryptoClasses`> <crée la cartographie entre le SHA256CryptoServiceProvider et le pseudonyme "SHA256CSP".</span><span class="sxs-lookup"><span data-stu-id="69d23-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="69d23-118">L’élément `nameEntry` <> crée la cartographie entre le pseudonyme "SHA256CSP" et l’URL `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`spécifiée .</span><span class="sxs-lookup"><span data-stu-id="69d23-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`.</span></span>  
  
 <span data-ttu-id="69d23-119">Pour enregistrer l'algorithme personnalisé en code, utilisez la méthode <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="69d23-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="69d23-120">Cette méthode crée ces deux mappages.</span><span class="sxs-lookup"><span data-stu-id="69d23-120">This method creates both mappings.</span></span> <span data-ttu-id="69d23-121">L'exemple suivant illustre l'appel de cette méthode :</span><span class="sxs-lookup"><span data-stu-id="69d23-121">The following example shows how to call this method:</span></span>  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="69d23-122">Configurer la liaison</span><span class="sxs-lookup"><span data-stu-id="69d23-122">Configure the Binding</span></span>  
 <span data-ttu-id="69d23-123">Vous pouvez configurer la liaison en spécifiant la classe personnalisée dérivée de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> dans les paramètres de liaison, comme indiqué dans l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="69d23-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="69d23-124">Pour un exemple de code complet, voir [l’agilité cryptographique dans l’échantillon WCF Security.](../samples/cryptographic-agility-in-wcf-security.md)</span><span class="sxs-lookup"><span data-stu-id="69d23-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69d23-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69d23-125">See also</span></span>

- [<span data-ttu-id="69d23-126">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="69d23-126">Securing Services and Clients</span></span>](../feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="69d23-127">Sécurisation de services</span><span class="sxs-lookup"><span data-stu-id="69d23-127">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="69d23-128">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="69d23-128">Security Overview</span></span>](../feature-details/security-overview.md)
- [<span data-ttu-id="69d23-129">Concepts de sécurité</span><span class="sxs-lookup"><span data-stu-id="69d23-129">Security Concepts</span></span>](../feature-details/security-concepts.md)
