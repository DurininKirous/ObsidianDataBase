behavior:
  scaleUp:
    policies:
    - type: Percent
      value: 100
      periodSeconds: 60
  scaleDown:
    policies:
    - type: Pods
      value: 2
      periodSeconds: 60

Контролирует, **насколько быстро** можно добавлять/убавлять поды.

[[Upscale Downscale Policy]]
[[HPA]]