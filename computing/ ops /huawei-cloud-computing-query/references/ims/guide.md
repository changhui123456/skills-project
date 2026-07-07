# IMS Python 脚本使用指南

---

## list_images.py — 查询镜像列表

作用：查询 IMS 镜像列表，包括 ID、名称、操作系统类型、操作系统位数、状态、imagetype、可见性。
用法详见：python scripts/ims/list_images.py -h

---

## list_image_by_tags.py — 按标签查询镜像

作用：按标签查询 IMS 镜像，包括 资源ID、资源名称、状态。
用法详见：python scripts/ims/list_image_by_tags.py -h

---

## list_image_members.py — 查询镜像成员列表

作用：查询 IMS 镜像成员列表，包括 member_id、状态、member_type、创建时间。
用法详见：python scripts/ims/list_image_members.py -h

---

## list_image_tags.py — 查询镜像标签

作用：查询 IMS 镜像标签，包括 键、值。
用法详见：python scripts/ims/list_image_tags.py -h

---

## list_images_tags.py — 查询租户所有镜像标签

作用：查询租户所有 IMS 镜像标签，包括 键、values。
用法详见：python scripts/ims/list_images_tags.py -h

---

## list_os_versions.py — 查询镜像支持的 OS 版本列表

作用：查询 IMS 镜像支持的 OS 版本列表，包括 平台、os_version_key、操作系统版本、操作系统位数、操作系统类型。
用法详见：python scripts/ims/list_os_versions.py -h

---

## list_tags.py — 查询租户镜像标签列表

作用：查询租户 IMS 镜像标签列表，包括 tag。
用法详见：python scripts/ims/list_tags.py -h

---

## show_image_quota.py — 查询镜像配额

作用：查询 IMS 镜像配额，包括 类型、已使用、配额、最小值、最大值。
用法详见：python scripts/ims/show_image_quota.py -h

---

## show_job.py — 查询异步任务信息

作用：查询 IMS 异步任务信息。
用法详见：python scripts/ims/show_job.py -h

---

## show_job_progress.py — 查询异步任务进度

作用：查询 IMS 异步任务进度。
用法详见：python scripts/ims/show_job_progress.py -h

---

## show_image.py — 查询镜像详情

作用：查询 IMS 镜像详情，包括 id、name、status、visibility、imagetype、protected、os_type、os_bit、os_version、platform、disk_format、min_disk、min_ram、image_size、created_at、updated_at、support_kvm、support_xen 等。
用法详见：python scripts/ims/show_image.py -h

---

## show_image_member.py — 查询镜像成员详情

作用：查询 IMS 镜像成员详情，包括 image_id、member_id、status、member_type、created_at、updated_at。
用法详见：python scripts/ims/show_image_member.py -h
