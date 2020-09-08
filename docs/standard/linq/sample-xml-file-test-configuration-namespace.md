---
title: 'Exemple de fichier XML : configuration de test dans un espace de noms-LINQ to XML'
description: Ce fichier XML, qui est utilisé dans les exemples, contient des données de configuration de test dans un espace de noms.
ms.date: 07/20/2015
ms.assetid: e75ad1bc-5636-4623-9a34-a286a8c485d6
ms.openlocfilehash: 2b45ff5196b572a9d1d3161de9470e8e48faa26f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553583"
---
# <a name="sample-xml-file-test-configuration-in-a-namespace-linq-to-xml"></a><span data-ttu-id="1ab62-103">Exemple de fichier XML : configuration de test dans un espace de noms (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="1ab62-103">Sample XML file: Test configuration in a namespace (LINQ to XML)</span></span>

<span data-ttu-id="1ab62-104">Le fichier XML suivant est utilisé dans différents exemples de la documentation de LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="1ab62-104">The following XML file is used in various examples in the LINQ to XML documentation.</span></span> <span data-ttu-id="1ab62-105">Il s'agit d'un fichier de configuration test.</span><span class="sxs-lookup"><span data-stu-id="1ab62-105">This is a test configuration file.</span></span> <span data-ttu-id="1ab62-106">Le code XML se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="1ab62-106">The XML is in a namespace.</span></span>

## <a name="testconfiginnamespacexml"></a><span data-ttu-id="1ab62-107">TestConfigInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="1ab62-107">TestConfigInNamespace.xml</span></span>

```xml
<?xml version="1.0"?>
<Tests xmlns="http://www.adatum.com">
  <Test TestId="0001" TestType="CMD">
    <Name>Convert number to string</Name>
    <CommandLine>Examp1.EXE</CommandLine>
    <Input>1</Input>
    <Output>One</Output>
  </Test>
  <Test TestId="0002" TestType="CMD">
    <Name>Find succeeding characters</Name>
    <CommandLine>Examp2.EXE</CommandLine>
    <Input>abc</Input>
    <Output>def</Output>
  </Test>
  <Test TestId="0003" TestType="GUI">
    <Name>Convert multiple numbers to strings</Name>
    <CommandLine>Examp2.EXE /Verbose</CommandLine>
    <Input>123</Input>
    <Output>One Two Three</Output>
  </Test>
  <Test TestId="0004" TestType="GUI">
    <Name>Find correlated key</Name>
    <CommandLine>Examp3.EXE</CommandLine>
    <Input>a1</Input>
    <Output>b1</Output>
  </Test>
  <Test TestId="0005" TestType="GUI">
    <Name>Count characters</Name>
    <CommandLine>FinalExamp.EXE</CommandLine>
    <Input>This is a test</Input>
    <Output>14</Output>
  </Test>
  <Test TestId="0006" TestType="GUI">
    <Name>Another Test</Name>
    <CommandLine>Examp2.EXE</CommandLine>
    <Input>Test Input</Input>
    <Output>10</Output>
  </Test>
</Tests>
```
