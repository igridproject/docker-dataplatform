# docker-dataplatform

## Kubernetes deployment (bsmain)

สำหรับ deploy service ในโฟลเดอร์ `bsmain` บน Kubernetes ให้ใช้ manifest ชุดนี้:

```bash
kubectl apply -f bsmain/k8s/bsmain-stack.yaml
```

สิ่งที่ถูกสร้าง:
- `Deployment` + `Service` ของ `bigstream`, `redis`, `rabbitmq`
- `PersistentVolumeClaim` สำหรับข้อมูล `bigstream` และ `redis`
- `ConfigMap` (`bigstream-acl`) สำหรับไฟล์ `acl.json`
- `Secret` (`bigstream-secret`) สำหรับค่า `BSCONFIG_SECRET_TEXT`

> ก่อนใช้งานจริง ควรแก้ค่าใน `Secret` และแทนค่า environment placeholders เช่น `${BIGSTREAM_IMG}`, `${BS_NUM_WORKER}`, `${BSCONFIG_KEYSTORE_DIR}`, `${REDIS_TAG}` ให้เหมาะกับ environment ของคุณ
