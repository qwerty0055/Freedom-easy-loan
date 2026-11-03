# Freedom-easy-loan
Give loans
// lib/utils/phone.ts
export function normalizeGhanaPhone(phone: string): string | null {
  // Remove spaces, hyphens, and leading plus
  let cleaned = phone.replace(/[\s\-\+]/g, '');

  // If local format (024XXXXXXX or 050XXXXXXX), strip leading '0' and append '233'
  if (/^0[2357]\d{8}$/.test(cleaned)) {
    return `233${cleaned.substring(1)}`;
  }

  // If already in international format (23324XXXXXXX)
  if (/^233[2357]\d{8}$/.test(cleaned)) {
    return cleaned;
  }

  return null; // Invalid Ghanaian mobile number format
}
