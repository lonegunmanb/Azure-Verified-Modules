---
title: Frequently Asked Questions (FAQs)
geekdocNav: true
geekdocAlign: left
geekdocAnchor: true
geekdocToC: 2
---

{{< hint type=tip >}}

Got an unanswered question? Create a [GitHub Issue](https://github.com/Azure/Azure-Verified-Modules/issues) so we can get it answered and added here for everyone's benefit 👍

{{< /hint >}}

{{< hint type=note >}}

**Microsoft FTEs only**: check out the [internal FAQ](https://dev.azure.com/CSUSolEng/Azure%20Verified%20Modules/_wiki/wikis/AVM%20Internal%20Wiki/353/(Internal-only)-Contributor-Q-A) for additional information.

{{< /hint >}}

{{< toc >}}

{{< hint type=tip >}}

Check out the [Contribution Q&A](/Azure-Verified-Modules/contributing/q-and-a/) for more answers to common questions about the contribution process.

{{< /hint >}}

## Timeline, history, plans

### When will we have a library that has a "usable" stand? Not complete, but the most important resources?

- **Bicep**: AVM leverages and evolves existing modules of [CARML](https://aka.ms/CARML) (Common Azure Resource Module Library) for its Bicep resource module collection (see [here](/Azure-Verified-Modules/faq/#carmltfvm-to-avm-evolution-details)). To initially populate AVM with Bicep resource modules, all  existing CARML modules will be migrated to AVM. See the [timeline and approach](/Azure-Verified-Modules/faq/#timeline-and-approach) section below for more details. Pattern modules can then be developed on top of these resource modules.
- **Terraform**: In case of Terraform, there are significantly less modules available in [TFVM](https://aka.ms/TFVM) (Terraform Verified Modules Library) compared to CARML, hence, Terraform modules are being built as people volunteer to be module owners. We're trying to prioritize the development of the Terraform modules based on our learnings from CARML - e.g. which ones are the most frequently deployed modules.

---

### What is happening to existing initiatives like CARML and TFVM?

The AVM initiative has been working closely with the teams behind the following initiatives:

- [CARML (Common Azure Resource Modules Library)](https://aka.ms/CARML)
- [TFVM (Terraform Verified Modules)](https://aka.ms/TFVM)
- [BRM (Bicep Registry Modules)](https://aka.ms/BRM) - this is where the AVM Bicep modules will be published.

AVM is a straight-line evolution of CARML & TFVM.

#### CARML/TFVM to AVM Evolution Details

While AVM Module contributions and ownership will shortly be opened to all Microsoft FTEs and the public (as contributors), the content of previously existing libraries such as TFVM & CARML will be migrated to AVM. The relevant teams are working out the details of the migration process as you read this.

In the case of CARML (Bicep), this will include:

- A new release making CARML conform with the Bicep Registry
- Tests automation alignment
- Module features added where applicable and aligned with AVM specifications

Aspiring Bicep-based AVM module contributors/owners, please check the CARML library first to see if the module you want to propose already exists as a CARML module.

- If you wish to own it in the future (once migrated by the AVM/CARML/TFVM teams), please go ahead and submit your Module Proposal using the form today and just let us know in the details
- If you don't plan to be the owner but do want to contribute, please hold off from contributing until it's migrated from CARML/TFVM

#### CARML Evolution

CARML is an existing IaC Bicep module library effort, that was started by ISD and has been contributed to by many across Microsoft and has also had some external contributions.

A lot of CARML's principles and architecture decisions will form the basis for AVM going forward. Most of the CARML modules today are very close to being AVM Resource Modules already and will only require a small number of changes to become AVM compliant.

CARML never got to the stage of creating, at scale, modules like AVM [Pattern Modules](/Azure-Verified-Modules/specs/shared/module-classifications), but they were on its long-term roadmap.

In summary, CARML will **evolve** to become the Bicep version of AVM. A notice will be placed on the CARML repo redirecting users and contributors to the AVM central repository as modules are evolved into AVM modules.​

##### CARML Publishing to Bicep Registry Notes

To avoid confusion for consumers it has been decided that CARML should not be published to the Bicep Registry under the CARML brand. Instead, the effort and work should be completed to take the existing CARML modules and perform a gap analysis upon them against the AVM specifications and then any required gaps addressed first.

At this stage the revamped module can be published to the Bicep Registry under the AVM brand to provide the uniform and single identity for AVM to consumers.

It may also be decided, for speed of delivery reasons, that a CARML module can be taken as is, with minimal AVM gaps addressed, and just rebranded to AVM and published to the Bicep Registry. However, this is ideally discouraged as it is creating technical debt from day 1.

Publishing both CARML and AVM to the Bicep Registry is wasted effort and will lead to confusion as they will overlap for 80% of their code and will leave consumers in an "analysis paralysis" scenario, which we must avoid.

##### Bicep Timeline and Approach

In Q4 of 2023, the AVM core team is planning to:

- Provide a detailed contribution guide for Bicep modules.
- Release the first version of the CI environment used for testing and publishing Bicep modules.
- Work out the details of and start delivering on a phased migration process.

Members of the CARML team have already volunteered to become module owners (see the module index of [Bicep resource modules](/Azure-Verified-Modules/indexes/bicep/bicep-resource-modules/)), and will be working with the AVM core team to migrate the existing CARML modules to AVM.

This will be done in a phased approach, as follows:

- The first phase including those CARML modules that other modules depend on, e.g., Public IP, NIC and Private Endpoint.
- A second phase including those modules that already have module owners associated, which will be migrated in a prioritized order based on customer demand, using telemetry.
- A third phase including the remaining of the CARML modules, not yet having a module owner associated.

Modules that won't have a module owner associated with them after they have been migrated to AVM will be marked as "[orphaned](/Azure-Verified-Modules/specs/shared/module-lifecycle/#orphaned-avm-modules)" and will be available for any Microsoft FTEs to pick up and become the module owner.

The AVM core team plans to have migrated the majority of the CARML modules to AVM by the end of 2023.

#### Terraform Timeline and Approach

As the [AVM core team](/Azure-Verified-Modules/specs/shared/team-definitions/#avm-core-team) is not directly responsible for the development of the modules (that's the responsibility of the [module owners](/Azure-Verified-Modules/specs/shared/team-definitions/#module-owners)), there's no specific timeline available for the publication of Terraform modules.

However, the AVM core team is focused on the following activities to facilitate and optimize the development process:

- Leveraging customer demand, telemetry and learnings from CARML to prioritize the development of Terraform modules.
- Providing automated tools and processes (CI environment and automated tests).
- Accelerating the build-out of the Terraform module owners' community.

---

### Will existing Landing Zone Accelerators (Platform & Application) be migrated to become AVM pattern modules and/or built from AVM resource modules?

Not in the short/immediate term. Existing Landing Zone Accelerators ([Platform](https://aka.ms/alz/aac#platform) & [Application](https://aka.ms/alz/aac#application)) will not be forced to convert their existing code bases, if available in either language, to AVM or to use AVM.

However, over time if new features or functionality are required by Landing Zone Accelerators, that team **SHOULD** consider migrating/refactoring that part of their code base to be constructed with the relevant AVM module if available. For example, the Bicep version of the "[Sub Vending](https://github.com/Azure/bicep-lz-vending)" solution is migrating to AVM shortly.

If the relevant AVM module isn't available to use to assist the Landing Zone Accelerator, then a new [AVM module proposal](https://aka.ms/avm/moduleproposal) should be made, and if desired, the Landing Zone Accelerator team may decide to own this proposed module 👍

---

### Does/will AVM cover Microsoft 365, Azure DevOps, GitHub, etc.?

While the principles and practices of AVM are largely applicable to other clouds and services such as, Microsoft 365 & Azure DevOps, the AVM program (today) only covers Azure cloud resources and architectures.

However, if you think this program, or a similar one, should exist to cover these other Microsoft Cloud offerings, please give a 👍 or leave a comment on this [GitHub Issue #71](https://github.com/Azure/Azure-Verified-Modules/issues/71) in the AVM repository.

---

### Will AVM also become a part of azd cli?

Yes, the AVM team is partnering with the AZD team and they are already using Bicep AVM modules from the public registry.

---

## Definitions, comparisons

### What is the difference between the Bicep Registry and AVM? (How) Do they come together?

The Public Bicep Registry (backed by the [BRM repository](https://aka.ms/BRM)) is Microsoft's official Bicep Registry for 1st party-supported Bicep modules. It has existed for a while now and has seen quite some contributions.

As various teams inside Microsoft have come together to establish a "One Microsoft" IaC approach and library, we started the AVM initiative to bridge the gaps by defining specifications for both Bicep and Terraform modules.

In the BRM repo today, "vanilla modules" (non-AVM modules) can be found in the `/modules` folder, while AVM modules are located in the `/avm` folder. Both are being published to the same endpoint, the Public Bicep Registry. AVM Bicep modules are published in a dedicated namespace, using the `avm/res` & `avm/ptn` prefixes to make them distinguishable from the Public Registry's "vanilla modules".

{{< hint type=note >}}

Going forward, AVM will become the single Microsoft standard for Bicep modules, published to the Public Bicep Registry, via the BRM repository.

In the upcoming period, existing "vanilla" modules will be retired or migrated to AVM, and new modules will be developed according to the AVM specifications.

{{< /hint >}}

---

### How is AVM different from Bicep private registries and TemplateSpecs? Is AVM related to, or separate from Azure Radius?

AVM - with its modules published in the Public Bicep Registry (backed by the [BRM repository](https://aka.ms/BRM)) - represents the only standard from Microsoft for Bicep modules in the Public Registry.

Bicep private registries and TemplateSpecs are different ways of inner-sourcing, sharing and internally leveraging Bicep modules within an organization. We're planning to provide guidance for theses scenarios in the future.

AVM has nothing to do with Radius (yet), but the AVM core team is constantly looking for additional synergies inside Microsoft.

---

### What does AVM mean by "WAF Aligned"?

{{< hint type=tip >}}

WAF == [Well-Architected Framework](https://learn.microsoft.com/azure/well-architected/) (as per our [glossary](/Azure-Verified-Modules/glossary/))

{{< /hint >}}

At a high-level "WAF Aligned" means, where possible and appropriate, AVM Modules will align to recommendations and default input parameter/variables to values that algin to WAF recommendations across all of it's pillars. For the security pillar we will also use the Microsoft Cloud Security Benchmark (MCSB) and Microsoft Defender for Cloud (MDFC) to align input parameter/variables values to these.

AVM will use the following sources to set it's "WAF Aligned" defaults:

- [Microsoft Azure Well-Architected Framework](https://learn.microsoft.com/azure/well-architected/)
- [Azure Proactive Resiliency Library](https://azure.github.io/Azure-Proactive-Resiliency-Library/)
- [Introduction to the Microsoft cloud security benchmark](https://learn.microsoft.com/security/benchmark/azure/introduction)
- [Security recommendations - Microsoft cloud security benchmark](https://learn.microsoft.com/azure/defender-for-cloud/recommendations-reference)

#### Will all AVM modules be 100% "WAF Aligned" out of the box and good to go?

Not quite, but they'll certainly be on the right path.

To understand this further you first must understand that some of the "WAF Aligned" recommendations, from the sources above are more than just setting a string or boolean value to something particular to meet the recommendation; some will require additional resources to be created and exist and then linked together to help satisfy the recommendation.

In these scenarios the AVM modules will not enforce the additional resources to be deployed and configured, but will provide sufficient flexibility via their input parameters/variables to be able to support the configuration, if so desired by the module consumer.

##### Some examples

| Recommendation                                                         | Will Be Set By Default in AVM Modules?                                                                            |
| ---------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| TLS version should always be set the latest/highest version TLS 1.3    | **Yes**, as string value                                                                                          |
| Key Vault should use RBAC instead of access policies for authorization | **Yes**, as string/boolean value                                                                                  |
| Container registries should use private link                           | **No**, as requires additional Private Endpoint and DNS configuration as well as, potentially, additional costs   |
| API Management services should use a virtual network                   | **No**, as requires additional Virtual Network and Subnet configuration as well as, potentially, additional costs |

{{< hint type=important >}}

While every Well-Architected Framework pillar's recommendations should equally be considered by the module owners/contributors, within AVM we are taking an approach to prioritize reliability and security over cost optimization. This provides consumers of the AVM modules, by default, more resilient and secure resources and patterns.

However, please note these defaulted values can be altered via input parameter/variables in each of the modules so that you can meet your specific requirements.

{{< /hint >}}

---

### What is a "Primary Resource" in the context of AVM?

The definition of a Primary Resource is detailed in the [glossary](/Azure-Verified-Modules/glossary/).

---

## Contribution, module ownership

### Can I be an AVM module owner if I'm not a Microsoft FTE?

Every module **MUST** have an owner who is responsible for module development and maintenance. One owner can own one or multiple modules. An owner can develop modules alone or lead a team that will develop a module.

Today, only Microsoft FTEs can be module owners. This is to ensure we can enforce and provide the long-term support required by this initiative.

However, you can still contribute to AVM as a non-Microsoft FTE. For more details, see [how you can contribute to AVM without being a module owner](/Azure-Verified-Modules/faq/#how-can-i-contribute-to-avm-without-being-a-module-owner) below.

---

### How can I contribute to AVM without being a module owner?

Yes, you can contribute to a module without being its owner, but you'll still need a module owner whom you can collaborate with. For context, see the answer to [this question](/Azure-Verified-Modules/faq/#can-i-be-an-avm-module-owner-if-im-not-a-microsoft-fte).

{{< hint type=tip >}}
If you're a Microsoft FTE, you should consider volunteering to be a module owner. You can propose a [new module](https://aka.ms/AVM/ModuleProposal), or look for [orphaned modules](https://aka.ms/AVM/OrphanedModules) and volunteer to be the owner for any of them.
{{< /hint >}}

If you're not a Microsoft FTE or don't want to be a module owner, you can still contribute to AVM. You have multiple options:

- You can propose a [new module](https://aka.ms/AVM/ModuleProposal) and provide as much context as possible under the "Module Details" section (e.g., why do you need the module, what's the business impact of not having it, etc.). The AVM core team will try to find a Microsoft FTE to be the module owner whom you can collaborate with.
- You can contact the current owner of any existing module and offer to contribute to it. You can find the current owners of all AVM modules in the [module indexes](/Azure-Verified-Modules/indexes/).
- You can look for [orphaned modules](https://aka.ms/AVM/OrphanedModules) and use the comment section to indicate that you'd be interested in contributing to this module, once a new owner is found.

---

### Are there different ways to contribute to AVM?

Yes, there are multiple ways to contribute to AVM. You can:

- [Propose](https://aka.ms/ModuleProposal) and develop a new module (Bicep or Terraform)
- Migrate an existing module from CARML (Bicep only) - look for modules to be migrated [here](https://azure.github.io/Azure-Verified-Modules/indexes/bicep/bicep-resource-modules/#planned-modules) and create a [module proposal](https://aka.ms/ModuleProposal) for the module you want to migrate.
- Become the owner of an orphaned module (mainly Bicep) - look for "orphaned module" issues [here](https://github.com/Azure/Azure-Verified-Modules/issues?q=is%3Aopen+is%3Aissue+label%3A%22Status%3A+Module+Orphaned+%3Aeyes%3A%22) or see the "Orphaned" swimlane [here](https://github.com/orgs/Azure/projects/529/views/1?filterQuery=is%3Aissue+is%3Aopen+is%3Aissue+is%3Aopen+label%3A%22Status%3A+Module+Orphaned+%3Aeyes%3A%22)

---

### Where can I find modules missing owners?

You can find modules missing owners in the following places:

- [All Orphaned modules](https://github.com/Azure/Azure-Verified-Modules/issues?q=is%3Aopen+is%3Aissue+label%3A%22Status%3A+Module+Orphaned+%3Aeyes%3A%22) or see the "Orphaned" swimlane [here](https://github.com/orgs/Azure/projects/529/views/1?filterQuery=is%3Aissue+is%3Aopen+is%3Aissue+is%3Aopen+label%3A%22Status%3A+Module+Orphaned+%3Aeyes%3A%22)
  - [Orphaned Bicep modules](https://github.com/Azure/Azure-Verified-Modules/issues?q=is%3Aopen+is%3Aissue+label%3A%22Status%3A+Module+Orphaned+%3Aeyes%3A%22+label%3A%22Language%3A+Bicep+%3Amuscle%3A%22+) or see the "Orphaned" swimlane [here](https://github.com/orgs/Azure/projects/529/views/1?filterQuery=is%3Aissue+is%3Aopen+is%3Aissue+is%3Aopen+label%3A%22Status%3A+Module+Orphaned+%3Aeyes%3A%22+label%3A%22Language%3A+Bicep+%3Amuscle%3A%22)
  - [Orphaned Terraform modules](https://github.com/Azure/Azure-Verified-Modules/issues?q=is%3Aopen+is%3Aissue+label%3A%22Status%3A+Module+Orphaned+%3Aeyes%3A%22+label%3A%22Language%3A+Terraform+%3Aglobe_with_meridians%3A%22) or see the "Orphaned" swimlane [here](https://github.com/orgs/Azure/projects/529/views/1?filterQuery=is%3Aissue+is%3Aopen+is%3Aissue+is%3Aopen+label%3A%22Status%3A+Module+Orphaned+%3Aeyes%3A%22+label%3A%22Language%3A+Terraform+%3Aglobe_with_meridians%3A%22+)
- [All modules looking for owners](https://github.com/Azure/Azure-Verified-Modules/issues?q=is%3Aopen+is%3Aissue+label%3A%22Needs%3A+Module+Owner+%3Amega%3A%22) or see the "Looking for owners" swimlane [here](https://github.com/orgs/Azure/projects/529/views/1?filterQuery=is%3Aissue+is%3Aopen+is%3Aissue+is%3Aopen+label%3A%22Needs%3A+Module+Owner+%3Amega%3A%22+)
  - [Bicep modules looking for owners](https://github.com/Azure/Azure-Verified-Modules/issues?q=is%3Aopen+is%3Aissue+label%3A%22Needs%3A+Module+Owner+%3Amega%3A%22+label%3A%22Language%3A+Bicep+%3Amuscle%3A%22) or see the "Looking for owners" swimlane [here](https://github.com/orgs/Azure/projects/529/views/1?filterQuery=is%3Aissue+is%3Aopen+is%3Aissue+is%3Aopen+label%3A%22Needs%3A+Module+Owner+%3Amega%3A%22+label%3A%22Language%3A+Bicep+%3Amuscle%3A%22)
  - [Terraform modules looking for owners](https://github.com/Azure/Azure-Verified-Modules/issues?q=is%3Aissue+is%3Aopen+label%3A%22Needs%3A+Module+Owner+%3Amega%3A%22+label%3A%22Language%3A+Terraform+%3Aglobe_with_meridians%3A%22+) or see the "Looking for owners" swimlane [here](https://github.com/orgs/Azure/projects/529/views/1?filterQuery=is%3Aissue+is%3Aopen+is%3Aissue+is%3Aopen+label%3A%22Needs%3A+Module+Owner+%3Amega%3A%22+label%3A%22Language%3A+Terraform+%3Aglobe_with_meridians%3A%22)

{{< hint type=note >}}

If any of these queries don't return any results, it means that no module in the selected category is missing its owner at the moment.

{{< /hint >}}

---

### I want to become the owner of XYZ modules, where can I indicate this, and what are the expected actions from me?

If exists, you can comment on the [Module Proposal issue](https://aka.ms/AVM/ModuleProposals) of the module that you are interested in and the AVM Core Team will do the triage providing information about next steps.

Having an understanding of roles & responsibilities is useful as well, you can find this information on the [Team Definitions & RACI | Azure Verified Modules](/Azure-Verified-Modules/specs/shared/team-definitions/) page.

---

### Can I submit a PR with new features to an existing module? If so, is this a good way to contribute too?

Of course! As all modules are open source, anyone can submit a PR to an existing module. But we'd suggest opening an issue first to discuss the suggested changes with the module owner before investing time in the code.

---

### Are there any videos on how to get started with contribution? E.g., how to set up a local environment for development, how to write a unit test etc.?

No videos on the technical details of contribution are available (yet), but a detailed, written guidance can be found for both Bicep and Terraform, here:

- [Bicep contribution guide](/Azure-Verified-Modules/contributing/bicep/)
- [Terraform contribution guide](/Azure-Verified-Modules/contributing/terraform/)

---

## Support

### Is AVM a Microsoft official service/product/library or is this classified as an OSS backed by Microsoft?

AVM is an officially supported OSS project from Microsoft, across all organizations.

AVM is owned, developed & supported by Microsoft, you may raise a GitHub issue on this repository or the module's repository directly to get support or log feature requests.

You can also log a support ticket and these will be redirected to the AVM team and the module owner(s).

See [Module Support](/Azure-Verified-Modules/help-support/module-support) for more information.

---

### So, does CSS support AVM?

Yes, and if they cannot resolve it (and/or it's not related to a Microsoft service/platform/api/etc.) they will pass the ticket to the module owner(s) to resolve.

For Microsoft FTEs only: see the **Internal** wiki for support workflow for more details -[AVM - Support Workflow - Overview](https://dev.azure.com/CSUSolEng/Azure%20Verified%20Modules/_wiki/wikis/AVM%20Internal%20Wiki/275/Azure-Verified-Module-Workflow)

---

## Technical questions

### Should pattern modules leverage resource modules? What if (some of) the required resource modules are not available?

The initial focus of development and migration from CARML/TFVM is mainly on resource modules. Once the most important resource modules are published, pattern modules can start leveraging them as and where needed. This however doesn't mean that the development of pattern modules is blocked in any way, since they may use native resources ("vanilla code"). If you're about to develop a pattern module and would need a resource modules that doesn't exist today, please consider building the resource module first, so that others can leverage it for their pattern modules as well.

Please see [PMNFR2](/Azure-Verified-Modules/specs/shared/#id-pmnfr2---category-composition---use-resource-modules-to-build-a-pattern-module) for more details.

---

### Does AVM have same limitations as ARM (4 MB) size and 255 parameters only?

Yes, as AVM is just a collection of official Bicep/Terraform modules, it still has same Bicep/Terraform language or Azure platform limitations.

---

### Does/will AVM support Managed Identity, and Microsoft Entra objects automation?

Managed Identities - Yes, they are supported in all resources today.
Entra objects - May come as new modules if/when the Graph provider will be released which is still in private preview.

---

### How does AVM ensure code quality?

AVM utilizes a number of validation pipelines for both Bicep and Terraform. These pipelines are run on every PR and ensure that the code is compliant with the AVM specifications and that the module is working as expected.

For example, in case of Bicep, as part of the [PR process](/Azure-Verified-Modules/contributing/bicep/bicep-contribution-flow/#6-create-a-pull-request-to-the-public-bicep-registry), we're asking contributors to provide a workflow status badge as a proof of successful validation using our testing pipelines.

The validation includes 2 main stages run in sequence:

- Static validation: to ensure that the module complies to AVM specifications.
- Deployment validation: to ensure all test examples are working from a deployment perspective.

These same validations are also run in the [BRM](https://aka.ms/BRM) repository after merge. The new version of the contributed module is published to the Public Bicep Registry only if all validations are successful.

---

## Using AVM

### How can I use Bicep modules through the Public Registry?

Use the [Bicep Visual Studio Code extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-bicep) to author your Bicep template and explore modules published in the Bicep Public Registry. For more details, see the the below example steps.

{{< hint type=note >}}
The Bicep VSCode extension is reading metadata through [this JSON file](https://live-data.bicep.azure.com/module-index). All modules are added to this file, as part of the publication process.
{{< /hint >}}

1. When authoring a new Bicep file, use the [VS Code extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-bicep) to explore the modules published in the Bicep Public Registry.
<img src="../img/faq/use-bicep-module-01.png" width=100%>

2. Expanding on this you can see the AVM modules that are published.
<img src="../img/faq/use-bicep-module-02.png" width=100%>

3. Selecting the module expands on the current available versions.
<img src="../img/faq/use-bicep-module-03.png" width=100%>

4. Setting required properties exposes what is required on the module.
<img src="../img/faq/use-bicep-module-04.png" width=100%>

5. Hovering over the `myTestModule` name exposes the module's documentation URL.
<img src="../img/faq/use-bicep-module-05.png" width=100%>

6. Clicking on the link opens up the Bicep Registry Repo for the AVM module's source code, where you can find the documentation detailing all the module's functionality, input parameters and outputs, while providing various examples.
<img src="../img/faq/use-bicep-module-06.png" width=100%>

---

### Aren't AVM resource modules too complex for people less skilled in IaC technologies?

 **TLDR**: Resource modules have complexity inside, so they can be flexibly used from the outside.

Resource modules are written in a flexible way; therefore, you don't need to modify them from project to project, use case to use case, as they aim to cover most of the functionality that a given resource type can provide, in a way that you can interact with any module just by using the required parameters - i.e., you don't have to know how the template of the particular module works inside, just take a look at the `README.md` file of the given module to learn how to leverage it.

Resource modules are multi-purpose; therefore, they contain a lot of dynamic expressions (functions, variables, etc.), so there's no need to maintain multiple instances for different use cases. They can be deployed in different configurations just by changing the input parameters. They should be perceived by the **user** as black boxes, where they don't have to worry about the internal complexity of the code, as they only interact with them by their parameters.

---

### Can I call a Bicep child module directly? E.g., can I update or add a secret in an existing Key Vault, or a route in an existing route table?

As per the way the Public Registry is implemented today, it is not possible to publish child-modules separate from its parents. As such, you cannot reference e.g. a `avm/res/key-vault/vault/key` module directly from the registry, but can only deploy it through its parent `avm/res/key-vault/vault` - UNLESS you actually grab the module folder locally.

However, we kept the door open to make this possible in the future if there is a demand for it.
