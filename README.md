# Robotic Microscopy & Automation for Quantum Materials Research

Modular sample storage, robotic microscope loading, and vision-based graphene flake identification for graphene and hexagonal boron nitride (hBN) research.

---

## System Design

### Modular Four-Chip Trays

The previous workflow required manually loading and scanning chips one at a time. I have developed CAD models for trays that each hold **four graphene or hBN chips**, providing a shared carrier for the planned automated microscopy workflow.

The tray holders are modular. Additional holder modules can be added to accommodate more trays, expanding storage capacity as the number of samples grows. Each fully populated tray adds four chip positions.

The design brings together:

- **Four-chip trays** for organizing samples in a shared carrier.
- **Modular tray holders** for expanding sample storage.
- **QR-based tray identification** for tracking samples and their storage locations.
- **Robotic transfer** between sample storage and the microscope.

### Tray and Holder CAD

<p align="center">
  <!-- <img src="media/modular-tray-cad.png" alt="CAD model of a four-chip tray and modular tray holder" width="750"/> -->
  <em>CAD image placeholder: four-chip tray and modular tray holder.</em>
</p>

---

## Robotic Pick-and-Place Setup

The planned setup uses an [Anvil OpenYAM](https://shop.anvil.bot/products/openyam) robotic arm for **vision-guided picking and placing** between the tray storage system and the microscope stage.

I am currently designing the arm algorithms and motion planning for this workflow. The goal is to replace repeated manual sample transfers with an organized sequence of automated microscope loading and unloading operations.

### Tray Identification and Visual Localization

QR codes will identify individual trays and associate them with their stored samples and locations. Camera images will also be used to estimate the positions of the trays and relevant pickup and placement locations.

The planned vision workflow combines **QR-based identification** with **pixel-level spatial localization**. Image coordinates will need to be mapped into the robot's coordinate frame through camera-to-robot calibration to guide the arm's motions. QR identity provides the organizational reference; visual localization provides the spatial information for picking and placing.

The intended workflow is:

```text
Identify Tray from QR Code
          ↓
Locate Pickup and Placement Targets in Camera Images
          ↓
Map Image Locations into Robot Coordinates
          ↓
Plan and Execute Pickup
          ↓
Place at the Microscope for Scanning
          ↓
Return to the Identified Storage Location
```

### Pick-and-Place Demonstration

<p align="center">
  <img src="media/PnP_demo.gif" alt="OpenYAM robotic pick-and-place demonstration" width="750"/>
</p>

---

## Graphene Flake Detection

Alongside the handling system, I have manually annotated **RGB microscopy images** to prepare a training dataset for an **Ultralytics YOLO11** vision model.

The annotations identify graphene flakes across different thickness categories and distinguish them from debris. The intended model will use these labels to detect candidate flakes and predict their annotated thickness categories from their appearance in microscope images.

This model is intended to support the selection of suitable flakes during microscope image review. It is a separate vision task from the camera-based localization used to guide the robotic arm.

### Manual Annotations

<p align="center">
  <!-- <img src="media/graphene-annotations.png" alt="Manually annotated RGB microscopy image showing graphene flake thickness categories and debris" width="750"/> -->
  <em>Image placeholder: manually annotated flakes, thickness categories, and debris.</em>
</p>

### Model Predictions

<p align="center">
  <!-- <img src="media/graphene-predictions.png" alt="YOLO11 model predictions for graphene flakes, thickness categories, and debris" width="750"/> -->
  <em>Image placeholder: model predictions, to be added after training and evaluation.</em>
</p>

---

## Current Development

| Component | Status |
| --- | --- |
| Four-chip trays and modular holders | CAD developed |
| Robotic arm algorithms and motion planning | In design |
| QR-based tray identification and visual localization | Planned |
| RGB microscopy dataset | Manual annotations created |
| YOLO11 flake and thickness-category detection | Training and evaluation planned |

---

## Hardware and Tools

- **Mechanical design:** CAD for four-chip trays and modular holders
- **Robotics:** Anvil OpenYAM
- **Tray organization:** QR codes
- **Microscopy vision:** RGB images, manual annotations, Ultralytics YOLO11

<!-- Media setup: add the referenced files under media/, uncomment each img element, and remove its placeholder caption. -->
