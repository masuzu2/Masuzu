<template>
    <div class="contact-form">
        <form @submit.prevent="submitForm" id="form">
            <div class="form-group">
                <label for="name">Name:</label>
                <input type="text" id="name" v-model="name" required />
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="email" v-model="email" required />
            </div>
            <div class="form-group">
                <label for="message">Message:</label>
                <textarea id="message" v-model="message" required></textarea>
            </div>
            <button type="submit" class="submit-button" :class="{ sending: isSending, sent: isSent }" id="button">Submit</button>
        </form>
        <div v-if="toastMessage" :class="['toast', toastType, { show: showToast }]">{{ toastMessage }}</div>
    </div>
</template>

<script setup>
useHead({
    title: 'Contact Me',
    meta: [
        {
            name: 'description',
            content: 'Contact Chinnapat Boonyod'
        },
    ]
});
import { ref, onMounted } from 'vue';

const name = ref('');
const email = ref('');
const message = ref('');
let emailjs;
const isSending = ref(false);
const isSent = ref(false);
const toastMessage = ref('');
const showToast = ref(false);
const toastType = ref('');

onMounted(async () => {
    emailjs = await import('emailjs-com');
    setupInputValidation();
});

const submitForm = () => {
    isSending.value = true;
    const templateParams = {
        name: name.value,
        email: email.value,
        message: message.value,
    };

    emailjs.send('service_a6yy5wk', 'template_kvbajgs', templateParams, 'b59DjgHlw6Ku42fDZ')
        .then((response) => {
            console.log('SUCCESS!', response.status, response.text);
            isSending.value = false;
            isSent.value = true;
            showToastMessage('Message sent successfully!', 'success');
        }, (error) => {
            console.log('FAILED...', error);
            isSending.value = false;
            showToastMessage('Failed to send message.', 'error');
        });
};

const showToastMessage = (message, type) => {
    toastMessage.value = message;
    toastType.value = type;
    showToast.value = true;
    setTimeout(() => {
        showToast.value = false;
    }, 3000);
};

const setupInputValidation = () => {
    document.querySelectorAll('.form-group input').forEach(input => {
        input.addEventListener('focus', () => {
            input.style.transform = 'scale(1.02)';
            input.style.boxShadow = '0 4px 12px rgba(33, 150, 243, 0.2)';
        });

        input.addEventListener('blur', () => {
            input.style.transform = 'scale(1)';
            input.style.boxShadow = 'none';
            validateInput(input);
        });

        input.addEventListener('input', (e) => {
            if (e.target.value.length > 0) {
                e.target.classList.add('has-content');
            } else {
                e.target.classList.remove('has-content');
            }
        });
    });
};

const validateInput = (input) => {
    if (input.type === 'email') {
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        if (!emailRegex.test(input.value)) {
            showInputError(input, 'Please enter a valid email');
            return false;
        }
    }
    if (input.value.trim() === '') {
        showInputError(input, 'This field is required');
        return false;
    }
    hideInputError(input);
    return true;
};

const showInputError = (input, message) => {
    const errorDiv = document.createElement('div');
    errorDiv.className = 'error-message';
    errorDiv.textContent = message;
    errorDiv.style.color = '#ff4444';
    errorDiv.style.fontSize = '12px';
    errorDiv.style.marginTop = '5px';
    errorDiv.style.opacity = '0';

    const parent = input.parentElement;
    const existing = parent.querySelector('.error-message');
    if (existing) parent.removeChild(existing);

    parent.appendChild(errorDiv);
    requestAnimationFrame(() => errorDiv.style.opacity = '1');
};

const hideInputError = (input) => {
    const errorDiv = input.parentElement.querySelector('.error-message');
    if (errorDiv) errorDiv.remove();
};
</script>

<style lang="scss" scoped>
.contact-form {
    max-width: 600px;
    margin: 0 auto;
    padding: 2rem;
    background: linear-gradient(135deg, #f0f8ff, #e6f7ff);
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    animation: fadeIn 1s ease-in-out, pulse 2s infinite;
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(-20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes pulse {
    0%, 100% {
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    50% {
        box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
    }
}

form {
    display: flex;
    flex-direction: column;
}

.form-group {
    margin-bottom: 1.5rem;
    position: relative;
}

label {
    margin-bottom: 0.5rem;
    font-weight: bold;
    color: #333;
    transition: color 0.3s;
}

input, textarea {
    width: 100%;
    padding: 0.75rem;
    border: 1px solid #add8e6;
    border-radius: 4px;
    transition: border-color 0.3s, box-shadow 0.3s, transform 0.3s;
}

input:focus, textarea:focus {
    border-color: #87cefa;
    box-shadow: 0 0 8px rgba(135, 206, 250, 0.5);
    outline: none;
    transform: scale(1.02);
}

.submit-button {
    padding: 0.75rem;
    border: none;
    border-radius: 4px;
    background-color: #87cefa;
    color: white;
    cursor: pointer;
    transition: background-color 0.3s, transform 0.3s;
}

.submit-button:hover {
    background-color: #00bfff;
    transform: translateY(-2px);
}

.toast {
    position: fixed;
    top: 20px;
    right: 20px;
    padding: 16px 24px;
    border-radius: 12px;
    background: rgba(33, 33, 33, 0.95);
    color: white;
    font-weight: 500;
    opacity: 0;
    transform: translateX(100%) translateY(-10px);
    transition: all 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
    backdrop-filter: blur(10px);
    box-shadow: 
        0 8px 20px rgba(0, 0, 0, 0.2),
        0 4px 12px rgba(0, 0, 0, 0.15);
    z-index: 1000;
}

.toast.show {
    opacity: 1;
    transform: translateX(0) translateY(0);
}

.toast.success {
    background: linear-gradient(135deg, rgba(102, 187, 106, 0.95), rgba(67, 160, 71, 0.95));
}

.toast.error {
    background: linear-gradient(135deg, rgba(239, 83, 80, 0.95), rgba(229, 57, 53, 0.95));
}

/* Responsive Design */
@media (max-width: 768px) {
    .contact-form {
        padding: 1rem;
    }

    .form-group {
        margin-bottom: 1rem;
    }

    .submit-button {
        padding: 0.5rem;
    }
}

@media (max-width: 480px) {
    .contact-form {
        padding: 0.5rem;
    }

    .submit-button {
        padding: 0.5rem;
        font-size: 0.875rem;
    }
}
</style>