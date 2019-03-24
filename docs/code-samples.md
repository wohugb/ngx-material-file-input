# 代码示例

## 简单的输入

```html
<mat-form-field>
  <ngx-mat-file-input formControlName="basicfile" placeholder="Basic Input" ></ngx-mat-file-input>
  <mat-icon matSuffix>folder</mat-icon>
</mat-form-field>
```

## 输入验证：required和maxSize

```ts
constructor(private _fb: FormBuilder) {}

ngOnInit() {
  this.formDoc = this._fb.group({
    requiredfile: [
      undefined,
      [Validators.required, FileValidator.maxContentSize(this.maxSize)]
    ]
  });
}
```

```html
<mat-form-field>
  <ngx-mat-file-input formControlName="requiredfile" placeholder="Required input" valuePlaceholder="No file selected" required></ngx-mat-file-input>
  <mat-icon matSuffix>folder</mat-icon>
  <mat-error *ngIf="formDoc.get('requiredfile').hasError('required')">
    请选择一个文件
  </mat-error>
  <mat-error *ngIf="formDoc.get('requiredfile').hasError('maxContentSize')">
    The total size must not exceed {{formDoc.get('requiredfile')?.getError('maxContentSize').maxSize | byteFormat}} ({{formDoc.get('requiredfile')?.getError('maxContentSize').actualSize
    | byteFormat}}).
  </mat-error>
</mat-form-field>
```

```json
{
  "required": true
}
```

## 禁用输入

```ts
constructor(private _fb: FormBuilder) {}

ngOnInit() {
  this.formDoc = this._fb.group({
    disabledfile: [{ value: undefined, disabled: true }]
  });
}
```

## 多输入

```html
<mat-form-field>
  <ngx-mat-file-input formControlName="multiplefile" placeholder="Multiple inputs" multiple></ngx-mat-file-input>
  <mat-icon matSuffix>folder</mat-icon>
</mat-form-field>
```

## 输入文件类型约束 (accept)

```html
<mat-form-field>
  <ngx-mat-file-input formControlName="acceptfile" placeholder="PDF file only" [accept]="'.pdf'"></ngx-mat-file-input>
  <mat-icon matSuffix>folder</mat-icon>
</mat-form-field>
```

## ByteFormat管道

```html
<p>A file size of {{ maxSize }} gives a human readable size of {{ maxSize | byteFormat }}</p>
```

A file size of 104857600 gives a human readable size of 100 MB