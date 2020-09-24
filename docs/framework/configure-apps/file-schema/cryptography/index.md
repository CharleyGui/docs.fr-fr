---
title: Schéma des paramètres de chiffrement
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: 0215851f83a13ee48547144f08c5c693ec2d90bf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149528"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="1478b-102">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="1478b-102">Cryptography Settings Schema</span></span>

<span data-ttu-id="1478b-103">Le schéma des paramètres de chiffrement contient des éléments qui spécifient comment mapper des noms d’algorithmes conviviaux à des classes qui implémentent des algorithmes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="1478b-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|<span data-ttu-id="1478b-104">Élément</span><span class="sxs-lookup"><span data-stu-id="1478b-104">Element</span></span>|<span data-ttu-id="1478b-105">Description</span><span class="sxs-lookup"><span data-stu-id="1478b-105">Description</span></span>|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|<span data-ttu-id="1478b-106">Contient une liste de classes de chiffrement qui ont un mappage à un nom convivial dans l' **\<nameEntry>** élément.</span><span class="sxs-lookup"><span data-stu-id="1478b-106">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptoClass**>](cryptoclass-element.md)|<span data-ttu-id="1478b-107">Contient une classe de chiffrement qui a un mappage à un nom convivial dans l' **\<nameEntry>** élément.</span><span class="sxs-lookup"><span data-stu-id="1478b-107">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|<span data-ttu-id="1478b-108">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="1478b-108">Contains cryptography settings.</span></span>|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|<span data-ttu-id="1478b-109">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="1478b-109">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="1478b-110">**\<mscorlib>** , élément pour les paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="1478b-110">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="1478b-111">Contient l' **\<cryptographySettings>** élément.</span><span class="sxs-lookup"><span data-stu-id="1478b-111">Contains the **\<cryptographySettings>** element.</span></span>|  
|[**\<nameEntry>**](nameentry-element.md)|<span data-ttu-id="1478b-112">Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="1478b-112">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[**\<oidEntry>**](oidentry-element.md)|<span data-ttu-id="1478b-113">Mappe un identificateur d’objet (OID) ASN.1 à un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="1478b-113">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[**\<oidMap>**](oidmap-element.md)|<span data-ttu-id="1478b-114">Contient les mappages d’OID ASN.1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="1478b-114">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1478b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1478b-115">See also</span></span>

- [<span data-ttu-id="1478b-116">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="1478b-116">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1478b-117">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="1478b-117">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
