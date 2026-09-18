# Cinemachine - Advanced Camera System

![Unity](https://img.shields.io/badge/Unity-2021.3%20LTS%2B-blue.svg)
![Cinemachine](https://img.shields.io/badge/Cinemachine-3.x-green.svg)
![Status](https://img.shields.io/badge/status-stable-success.svg)
![Documentation](https://img.shields.io/badge/docs-complete-brightgreen.svg)

English | [简体中文](./README-CN.md) | [Return to Main](../README.md)

## Overview

Cinemachine is Unity's advanced camera system that provides procedural camera behavior and dynamic shot composition.

---

## Core Architecture

Cinemachine consists of three core components:

#### 1. Unity Camera
- Physical camera that captures the scene
- Only one needed per setup
- Rendering endpoint for all virtual cameras

#### 2. Cinemachine Brain
- Component attached to Unity Camera
- Monitors all active virtual cameras
- Handles smooth transitions
- Timeline has higher priority

#### 3. Virtual Cameras
- One or more cameras defining behaviors
- Override Unity Camera when active
- Switch based on priority and game state

---

## How It Works

Cinemachine Brain evaluates all virtual cameras and blends between them based on priority.

---

## Camera Transitions

- **Instant:** Immediate cut
- **Timed:** Smooth blend over duration

---

## Quick Start

1. Add Cinemachine Brain to Main Camera
2. Create Virtual Camera in scene
3. Configure follow and look-at targets
4. Adjust camera properties

---

## Resources

- [Official Documentation](https://docs.unity3d.com/Packages/com.unity.cinemachine@latest)
- [Unity Learn Tutorials](https://learn.unity.com/search?k=cinemachine)
- [Pan & Tilt Controls](./Reference/Pan%20Tilt.md)
