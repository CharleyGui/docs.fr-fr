---
title: Élément <xmlSerializer>
description: L' <xmlSerializer> élément spécifie si une vérification supplémentaire de la progression du XmlSerializer est effectuée.
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 667d59f7eb0d1c7682afcdda584cc5b0ca2da802
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288925"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="c0cea-103">Élément \<xmlSerializer></span><span class="sxs-lookup"><span data-stu-id="c0cea-103">\<xmlSerializer> Element</span></span>
<span data-ttu-id="c0cea-104">Spécifie si un contrôle supplémentaire de la progression de <xref:System.Xml.Serialization.XmlSerializer> est effectué.</span><span class="sxs-lookup"><span data-stu-id="c0cea-104">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 \<configuration>  
\<system.xml.serialization>  
  
## <a name="syntax"></a><span data-ttu-id="c0cea-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0cea-105">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0cea-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c0cea-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c0cea-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c0cea-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0cea-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="c0cea-108">Attributes</span></span>  
  
|<span data-ttu-id="c0cea-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c0cea-109">Attribute</span></span>|<span data-ttu-id="c0cea-110">Description</span><span class="sxs-lookup"><span data-stu-id="c0cea-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0cea-111">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="c0cea-111">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="c0cea-112">Spécifie si la progression de <xref:System.Xml.Serialization.XmlSerializer> est vérifiée.</span><span class="sxs-lookup"><span data-stu-id="c0cea-112">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="c0cea-113">Affectez "true" ou "false" à l'attribut.</span><span class="sxs-lookup"><span data-stu-id="c0cea-113">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="c0cea-114">La valeur par défaut est "true".</span><span class="sxs-lookup"><span data-stu-id="c0cea-114">The default is "true".</span></span>|  
|<span data-ttu-id="c0cea-115">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="c0cea-115">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="c0cea-116">Spécifie si <xref:System.Xml.Serialization.XmlSerializer> utilise la génération de sérialisation héritée qui génère des assemblys en écrivant le code C# dans un fichier, puis en le compilant dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="c0cea-116">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="c0cea-117">La valeur par défaut est **false**.</span><span class="sxs-lookup"><span data-stu-id="c0cea-117">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0cea-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c0cea-118">Child Elements</span></span>  
 <span data-ttu-id="c0cea-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c0cea-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0cea-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c0cea-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c0cea-121">Élément</span><span class="sxs-lookup"><span data-stu-id="c0cea-121">Element</span></span>|<span data-ttu-id="c0cea-122">Description</span><span class="sxs-lookup"><span data-stu-id="c0cea-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0cea-123">\<system.xml.serialization>Appartient</span><span class="sxs-lookup"><span data-stu-id="c0cea-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="c0cea-124">Contient des paramètres de configuration pour les classes <xref:System.Xml.Serialization.XmlSerializer> et <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="c0cea-124">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0cea-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="c0cea-125">Remarks</span></span>  
 <span data-ttu-id="c0cea-126">Par défaut, le <xref:System.Xml.Serialization.XmlSerializer> fournit une couche supplémentaire de sécurité contre des attaques par déni de service potentielles lors de la désérialisation de données non fiables.</span><span class="sxs-lookup"><span data-stu-id="c0cea-126">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="c0cea-127">Pour ce faire, il tente de détecter des boucles infinies pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="c0cea-127">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="c0cea-128">Si une telle condition est détectée, une exception est levée avec le message suivant : « Erreur interne : la désérialisation n’a pas pu avancer sur le flux de données sous-jacent. ».</span><span class="sxs-lookup"><span data-stu-id="c0cea-128">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="c0cea-129">Le fait de recevoir ce message n'indique pas nécessairement qu'une attaque par déni de service est en cours.</span><span class="sxs-lookup"><span data-stu-id="c0cea-129">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="c0cea-130">Dans de rares circonstances, le mécanisme de détection de boucles infinies génère un faux positif et l'exception est levée pour un message entrant légitime.</span><span class="sxs-lookup"><span data-stu-id="c0cea-130">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="c0cea-131">Si vous voyez, dans votre application, que des messages légitimes sont rejetés par cette couche de protection supplémentaire, définissez l’attribut **checkDeserializeAdvances** sur la valeur false.</span><span class="sxs-lookup"><span data-stu-id="c0cea-131">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0cea-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="c0cea-132">Example</span></span>  
 <span data-ttu-id="c0cea-133">L’exemple de code suivant assigne la valeur false à l’attribut **checkDeserializeAdvances**.</span><span class="sxs-lookup"><span data-stu-id="c0cea-133">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0cea-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0cea-134">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="c0cea-135">\<system.xml.serialization>Appartient</span><span class="sxs-lookup"><span data-stu-id="c0cea-135">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
- [<span data-ttu-id="c0cea-136">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="c0cea-136">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
