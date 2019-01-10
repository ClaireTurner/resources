---



copyright:

  years: 2017, 2018
lastupdated: "2018-11-15"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:note: .note}

# 管理资源组
{: #rgs}

资源组是一种使用可定制的分组来组织帐户资源的方法，可帮助您一次性快速为用户分配对多个资源的访问权。使用 {{site.data.keyword.Bluemix}} Identity and Access Management (IAM) 访问控制来管理的任何帐户资源都属于您帐户中的资源组。Cloud Foundry 服务会分配给组织和空间，并且无法添加到资源组。

要开始管理资源组，请转至**管理** &gt; **帐户**。展开**帐户资源**，然后选择**资源组**。在其中，可以查看资源组，添加资源，对资源组重命名以及创建新资源组。有关使用资源组的更多信息，请参阅[使用资源组来组织资源的最佳实践](/docs/resources/bestpractice_rgs.html#bp_resourcegroups)。


## 创建资源组

如果您拥有现买现付或预订帐户，那么可以创建多个资源组，从而轻松地管理配额和查看一组资源的计费使用情况。您还可以对资源进行分组，更轻松地为用户一次性分配对多个实例的访问权。值得注意的是，在创建资源组后，可进行重命名，但是无法删除资源组。

如果您拥有轻量帐户或 30 天试用帐户，那么不能创建额外的资源组，但可以重命名缺省资源组。

资源组与 Cloud Foundry 组织或空间之间的连接受您的配额限制。有关更多信息，请参阅[什么是别名？](/docs/resources/connecting_apps.html#what_is_alias)。
{: note}

1. 转至**管理** &gt; **帐户**。展开**帐户资源**，然后选择**资源组**。 
2. 单击**创建资源组**。
3. 输入资源组的名称。
4. 单击**添加**。

## 向资源组添加资源

使用 IAM 管理的服务属于资源组，而不属于 Cloud Foundry 组织或空间。在目录中为其中一个服务创建服务实例时，系统会提示您将该实例分配给资源组。创建实例时选择的资源组是最终选择，无法更改。

## 查看资源组中的资源

为了方便地查看资源组中包含的资源，请在资源列表中按资源组进行过滤。

## 重命名资源组

已为您创建第一个资源组并命名为 `Default`。您可以选择更新此组或您所创建的任何其他组的名称。

1. 转至**管理** &gt; **帐户**。展开**帐户资源**，然后选择**资源组**。 
2. 从**操作** ![“操作列表”图标](../icons/action-menu-icon.svg) 菜单中选择**重命名**。
3. 输入唯一名称，然后单击**保存**。

## 使用 {{site.data.keyword.Bluemix_notm}} CLI 管理资源组和资源

{{site.data.keyword.Bluemix_notm}} CLI 有多个命令可支持资源管理。有关更多信息，请参阅[使用资源和资源组](/docs/cli/reference/ibmcloud/cli_resource_group.html#ibmcloud_commands_resource)。

## 管理对资源组的访问权

通过 Cloud IAM，您可以灵活地对帐户中资源的用户访问权进行细颗粒度的控制。您可以使用 Cloud IAM 为用户分配策略，以向用户提供对资源组中所有资源的访问权、对资源组中单个服务类型的访问权或对帐户中单个服务实例的访问权。向用户提供对资源组中资源的访问权，并不会授予用户管理资源组本身的访问权。您可以分别设置用于查看、编辑和管理实际资源组的访问权。

有关更多信息，请参阅[管理对资源的访问权](/docs/iam/mngiam.html#iammanidaccser)。
