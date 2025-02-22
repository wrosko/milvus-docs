---
id: home.md
---

<div class="doc-h1-wrapper">

  <div class="title">
    Welcome to Milvus Docs!
  </div>

  <div class="sub-title">
    Here you will learn about what Milvus is, and how to install, use, and deploy Milvus to build an application according to your business need.
  </div>

</div>

## Get Started

<div class="card-wrapper">

<div class="start_card_container">
  <a href="install_standalone-docker.md">
    <img  src="../../../assets/home_install.svg" alt="icon" />
    <p class="link-btn">Install Milvus <i class="fas fa-chevron-right"></i></p>
  </a>
  <p>Learn how to install Milvus using either Docker Compose or on Kubernetes.</p>
</div>

<div class="start_card_container">
  <a href="example_code.md">
    <img  src="../../../assets/home_quick_start.svg" alt="icon" />
    <p class="link-btn">Quick Start <i class="fas fa-chevron-right"></i></p>
  </a>
  <p>Learn how to quickly run Milvus with sample code.</p>
</div>

<div class="start_card_container">
  <a href="/bootcamp">
    <img  src="../../../assets/home_bootcamp.svg" alt="icon" />
    <p class="link-btn">Bootcamp <i class="fas fa-chevron-right"></i></p>
  </a>
  <p>
  Learn how to build vector similarity search applications with Milvus.
  </p>
</div>

</div>

<div class="milmi-tip">
  <p>
    Feel free to ask MilMi at the bottom right or submit an issue via GitHub by using the buttons at the top right of each page.
  </p>
  <img  src="../../../assets/MilMil.svg" alt="MilMil" />
</div>

## Recommended articles

<div class="doc-home-recommend-section">

<div class="recomment-item">
  <p>Use</p>

- [Create a Collection](create_collection.md)
- [Insert Data](insert_data.md)
- [Build an Index](build_index.md)
- [Vector Similarity Search](search.md)
- [Query](query.md)
</div>

<div class="recomment-item">
  <p>Deploy</p>

- [Configure Milvus](configure-docker.md)
- [Deploy on Clouds](aws.md)
- [Scale a Milvus Cluster](scaleout.md)
- [Set up storage](deploy_s3.md)
- [Monitor and Alert](monitor_overview.md)
</div>

<div class="recomment-item">
  <p>Learn</p>
- [System Configuration](system_configuration.md)
- [Architecture Overview](architecture_overview.md)
- [Vector Index](index_selection.md)
- [Similarity Metrics](metric.md)
- [Glossary](glossary.md)
</div>

</div>

<div class="doc-home-what-is-new">

## What's new in docs

_Jan 2022_

- Milvus announced its general availability release [Milvus 2.0.0](release_notes.md).
- Added guidance on installing a Milvus standalone with [APT or YUM](install_standalone-aptyum.md).
- Added documentation on how to [configure Milvus](configure-docker.md).
- Added the installation guide for Milvus [GO SDK](install-go.md) and [Java SDk](install-java.md).
- Add sample code in GO and Java in User Guide.

_Dec 2021_

- With the release of [Milvus 2.0-PreGA](release_notes.md), we have published new user guides concerning the new features of [Data Deletion](delete_data.md) and [Collection Alias](collection_alias.md).
- Updated [Search with Time Travel](timetravel.md) by introducing how to [generate a timestamp](timetravel.md#Generate-a-timestamp-for-search) based on an existing timestamp, Unix Epoch time, or date time.
- Added documentation about the newly released Milvus ecosystem tool, [Attu](attu.md). Learn what Attu is, and how to [install](attu_install-docker.md) and [use](attu_overview.md) it.
- Remade [Hello Milvus](example_code.md) to demonstrate the new feature of Data Deletion.
- Added a reference documentation explaining the mechanism of [Time Travel](timetravel_ref.md) in Milvus.

</div>
