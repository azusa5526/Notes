# Vitest notes

## 函數

函數分為物件監聽(Spy)與物件模擬兩種

- 物件監聽

  Vi.spyOn() 監聽對象為一個物件，只需要知道函數是否被呼叫時使用，無法替換函數實作。

- 物件模擬

  Vi.fn() 建立一個假的函數，替換函數實作。

## Mock

### vi.mock

替換掉某個 import 進來的模組，並且會提升到檔案的頂部，在所有 import 之前被執行。

```ts
vi.mock("@/api/dashboard", () => ({
  getDashboardApps: vi.fn(),
  getDashboardImage: vi.fn(),
}));
```

如果只想 mock 掉這個模組的某一個部分，可以使用 vi.importActual 引入原始模組，並單獨替換掉想要模擬的部分。

```ts
vi.mock("@/api/dashboard", async () => {
  const mod = (await vi.importActual("@/api/dashboard")) as any;
  return { ...mod, updateDashboardImage: vi.fn() };
});
```

### vi.doMock

與 vi.mock 相同，但不會提升到檔案的頂部。

### vi.mocked

TS 的型別助手，不會 mock 任何東西，只會回傳傳遞的物件。

主要是 TS 不知道目標物已經被 Mock 了，不認識 mock 方法，使用 vi.mocked 可以使 ts 認得這個被 mock 的東西。

### vi.resetAllMocks

清除所有 mock 的歷史紀錄，恢復成一個空函式

## 計時器

### vi.useFakeTimers

將計時器換為假的計時器，之後可以呼叫假計時器的方法，目前有用於 Vee-validate 需要經過 16ms 才驗證的的問題。

### vi.advanceTimersByTime

推進假計時器一段時間。

### vi.runAllTimers

推進所有已啟動的假計時器。

### vi.useRealTimers

恢復使用正常的計時器

```ts
vi.useFakeTimers();
...
// 填入了某些 Vee-validate 表單

await flushPromises();
vi.runAllTimers();
// 讓 Vee-validate 計時器啟動並完成驗證
await flushPromises();

expect(createRoleSpy).toBeCalledWith(expectFormValue);
vi.useRealTimers();
```
