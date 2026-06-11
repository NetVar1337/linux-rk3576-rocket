# RK3576 enablement for the mainline `rocket` NPU driver

A 4-patch RFC series adding Rockchip RK3576 support to the mainline `rocket`
NPU driver (`drivers/accel/rocket`), against `torvalds/master`.

Apply with `git am *.patch` onto a recent mainline tree.

```
0001  dt-bindings: npu: rockchip,rk3588-rknn-core: add RK3576 (conditional sram-supply)
0002  accel/rocket: look up core clocks by name (fixes clk_bulk .id never set)
0003  accel/rocket: add support for the RK3576 (per-SoC match data + PC_DONE polling)
0004  arm64: dts: rockchip: add RKNN core nodes to rk3576
```

**Status: compile-tested only, no RK3576 hardware.** `rocket` builds clean at
`W=1`, all ten rk3576 board dtbs build, `dt_binding_check` and `CHECK_DTBS`
pass (including a negative test that `sram-supply` is rejected on RK3576).
Builds on @gahingwoo's Rock 4D bring-up and the dri-devel prior art from
Nicolas Frattaroli / Tomeu Vizoso. See the cover letter (0000) for open items.
