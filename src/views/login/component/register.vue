<template>
    <el-form size="large" class="register-content-form">
        <el-form-item class="register-animation1">
            <el-input text :placeholder="$t('message.register.placeholder1')" v-model="state.ruleForm.mailPrefix"
                      clearable
                      autocomplete="off">
                <template #prefix>
                    <i class="fa fa-envelope-square"></i>
                </template>
                <template #append>
                    <el-select v-model="state.ruleForm.mailSuffix" placeholder="Select" style="width: 120px">
                        <el-option label="@163.com" value="@163.com"/>
                        <el-option label="@126.com" value="@126.com"/>
                        <el-option label="@yeah.net" value="@yeah.net"/>
                    </el-select>
                </template>
            </el-input>
        </el-form-item>
        <el-form-item class="register-animation2">
            <el-input
                    :type="state.isShowPassword ? 'text' : 'password'"
                    :placeholder="$t('message.register.placeholder2')"
                    v-model="state.ruleForm.password"
                    autocomplete="off"
            >
                <template #prefix>
                    <el-icon class="el-input__icon">
                        <ele-Unlock/>
                    </el-icon>
                </template>
                <template #suffix>
                    <i
                            class="iconfont el-input__icon login-content-password"
                            :class="state.isShowPassword ? 'icon-yincangmima' : 'icon-xianshimima'"
                            @click="state.isShowPassword = !state.isShowPassword"
                    >
                    </i>
                </template>
            </el-input>
        </el-form-item>
        <el-form-item class="register-animation3">
            <el-button round type="danger" v-waves class="register-content-submit">
                <span>{{ $t('message.register.btnText') }}</span>
            </el-button>
        </el-form-item>
    </el-form>
</template>

<script setup lang="ts" name="Register">
import {reactive} from 'vue';

// 定义变量内容
const state = reactive({
    isShowPassword: false,
    ruleForm: {
        mailPrefix: '',
        mailSuffix: '@163.com',
        password: '',

    },
});
</script>

<style scoped lang="scss">
.register-content-form {
  margin-top: 20px;
  @for $i from 1 through 4 {
    .register-animation#{$i} {
      opacity: 0;
      animation-name: error-num;
      animation-duration: 0.5s;
      animation-fill-mode: forwards;
      animation-delay: calc($i/10) + s;
    }
  }

  .register-content-code {
    width: 100%;
    padding: 0;
  }

  .register-content-submit {
    width: 100%;
    letter-spacing: 2px;
    font-weight: 300;
    margin-top: 15px;
  }

  .register-msg {
    color: var(--el-text-color-placeholder);
  }
}
</style>
